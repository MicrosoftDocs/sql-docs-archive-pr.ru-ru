---
title: Загрузка выхода локального пакета | Документы Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data flow [Integration Services], loading results
- loading data flow results
ms.assetid: aba8ecb7-0dcf-40d0-a2a8-64da0da94b93
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6799e593ab9d5ae1a9358bf54f4927838991ebd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740142"
---
# <a name="loading-the-output-of-a-local-package"></a>Загрузка выхода локального пакета
  Клиентские приложения могут считывать значения на выходе пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], если этот выход сохранен в назначения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием [!INCLUDE[vstecado](../../includes/vstecado-md.md)], либо если выход сохранен в назначение "Неструктурированный файл" с использованием классов в пространстве имен **System.IO**. Кроме того, клиентское приложение может считывать выход пакета непосредственно из памяти, без необходимости промежуточного шага для сохранения данных. Ключом к этому решению является `Microsoft.SqlServer.Dts.DtsClient` пространство имен, которое содержит специализированные реализации `IDbConnection` `IDbCommand` интерфейсов, и **IDbDataParameter** из пространства имен **System. Data** . По умолчанию сборка Microsoft.SqlServer.Dts.DtsClient.dll устанавливается в каталог **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.

> [!NOTE]
>  Для процедуры, описанной в этом разделе, необходимо, чтобы свойству DelayValidation задачи потока данных и любых родительских объектов было присвоено значение по умолчанию**False**.

## <a name="description"></a>Описание
 В этой процедуре демонстрируется, как разработать на управляемом коде клиентское приложение, которое загружает выход пакета с назначением DataReader непосредственно из памяти. Описанные здесь шаги демонстрируются в следующем образце кода.

#### <a name="to-load-data-package-output-into-a-client-application"></a>Загрузка данных с выхода пакета в клиентское приложение

1.  В пакете настройте назначение DataReader для получения выхода, который необходимо считать в клиентском приложении. Дайте назначению DataReader описательное имя, поскольку оно понадобится в дальнейшем для использования в клиентском приложении. Запомните имя назначения DataReader.

2.  В проекте разработки задайте ссылку на `Microsoft.SqlServer.Dts.DtsClient` пространство имен, найдя сборку **Microsoft.SqlServer.Dts.DtsClient.dll**. По умолчанию эта сборка устанавливается в **C:\Program Files\Microsoft SQL Server\100\DTS\Binn**. Импортируйте пространство имен в код с помощью C# `Using` или [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] `Imports` инструкции.

3.  В коде создайте объект типа `DtsClient.DtsConnection` со строкой подключения, содержащей параметры командной строки, необходимые **dtexec.exe** для запуска пакета. Дополнительные сведения см. в статье [dtexec Utility](../packages/dtexec-utility.md). Затем откройте соединение с помощью этой строки подключения. Можно также использовать программу **dtexecui** для создания необходимой строки подключения в визуальном режиме.

    > [!NOTE]
    >  В образце кода демонстрируется загрузка пакета из файловой системы с использованием синтаксиса `/FILE <path and filename>`. Однако можно также загрузить пакет из базы данных MSDB с помощью синтаксиса `/SQL <package name>` или из хранилища пакетов служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] с помощью синтаксиса `/DTS \<folder name>\<package name>`.

4.  Создайте объект типа `DtsClient.DtsCommand`, использующий ранее созданный объект `DtsConnection`, и присвойте его свойству `CommandText` в качестве значения имя назначения DataReader в пакете. Затем вызовите метод `ExecuteReader` командного объекта, чтобы загрузить результаты пакета в новое назначение DataReader.

5.  При необходимости можно косвенно параметризовать выход пакета с использованием коллекции объектов `DtsDataParameter` для объекта `DtsCommand`, чтобы передать значения переменным, определенным в пакете. В рамках пакета можно использовать эти переменные в качестве параметров запроса или в выражениях для воздействия на результаты, возвращаемые в назначение DataReader. Эти переменные необходимо определить в пакете в пространстве имен **DtsClient** , прежде чем их можно будет использовать с `DtsDataParameter` объектом из клиентского приложения. (Чтобы отобразить столбец **пространство имен** , может потребоваться нажать кнопку панели инструментов **Выбор столбцов переменных** в окне **переменные** .) В коде клиента при добавлении `DtsDataParameter` в `Parameters` коллекцию объекта не `DtsCommand` указывайте ссылку на пространство имен DtsClient из имени переменной. Пример:

    ```
    command.Parameters.Add(new DtsDataParameter("MyVariable", 1));
    ```

6.  Вызовите метод `Read` назначения DataReader повторно по мере необходимости для прохождения цикла по строкам выходных данных. Используйте эти данные или сохраните их для дальнейшего использования в клиентском приложении.

    > [!IMPORTANT]
    >  Метод `Read` в этой реализации назначения DataReader возвращает значение `true` еще раз после считывания последней строки данных. Возникают сложности с использованием обычного кода, реализующего цикл по назначению DataReader, пока метод `Read` возвращает значение `true`. Если пользовательским кодом предпринимается попытка закрыть назначение DataReader или соединение после считывания ожидаемого количества строк без дополнительного итогового вызова метода `Read`, будет выдано необработанное исключение. Однако если в коде предпринята попытка чтения данных в ходе этой последней итерации по циклу, метод `Read` все так же возвращает значение `true`, но после передачи последней строки кодом будет выдано необработанное исключение `ApplicationException` с сообщением, «Объект IDataReader служб SSIS находится за пределами результирующего набора». Это поведение отличается от остальных реализаций назначения DataReader. Поэтому при использовании цикла для считывания строк в назначении DataReader, когда метод `Read` возвращает значение `true`, необходимо написать код для захвата, тестирования и отмены ожидаемого исключения `ApplicationException` в ходе последнего успешного вызова метода `Read`. Либо, если заранее известно число ожидаемых строк, можно обработать строки, а затем вызвать метод `Read` еще раз перед закрытием назначения DataReader и соединения.

7.  Вызовите метод `Dispose` объекта `DtsCommand`. Это особенно важно, если были использованы какие-либо из объектов `DtsDataParameter`.

8.  Закройте назначение DataReader и объекты соединения.

## <a name="example"></a>Пример
 В следующем примере выполняется пакет, который вычисляет единственное статистическое значение и сохраняет его в назначение DataReader, а затем считывает значение из DataReader и отображает его в текстовом поле в форме Windows.

 Использование параметров не требуется при загрузке выхода пакета в клиентское приложение. Если вы не хотите использовать параметр, можно опустить использование переменной в пространстве имен **DtsClient** и опустить код, использующий `DtsDataParameter` объект.

#### <a name="to-create-the-test-package"></a>Создание тестового пакета

1.  Создайте новый пакет служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. В образце кода в качестве имени пакета используется «DtsClientWParamPkg.dtsx».

2.  Добавьте переменную типа String в пространство имен DtsClient. В образце кода в качестве имени переменной используется «Country». (Может понадобиться нажать кнопку панели инструментов **Выбор столбцов переменных** в окне **Переменные**, чтобы отобразить столбец **Namespace**.)

3.  Добавьте диспетчер соединений OLE DB, соединяющийся с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].

4.  Добавьте задачу потока данных в пакет и переключитесь в область конструктора потока данных.

5.  Добавьте источник OLE DB в поток данных и настройте его для использования ранее созданного диспетчера соединений OLE DB, затем выполните следующую команду SQL:

    ```
    SELECT * FROM Sales.vIndividualCustomer WHERE CountryRegionName = ?
    ```

6.  Щелкните `Parameters` и в диалоговом окне **Установка параметров запроса** сопоставьте один входной параметр в запросе Parameter0 с переменной DtsClient:: Country.

7.  Добавьте преобразование «Статистическая обработка» в поток данных и соедините выход источника OLE DB с этим преобразованием. Откройте редактор преобразования "Статистическая обработка" и настройте его для выполнения операции "подсчет всех" во всех входных столбцах (*) и вывода агрегированного значения с псевдонимом Кустомеркаунт.

8.  Добавьте назначение DataReader в поток данных и соедините выход преобразования «Статистическая обработка» с назначением DataReader. В образце кода в качестве имени назначения DataReader используется «DataReaderDest». Укажите единственный доступный входной столбец, CustomerCount, в качестве назначения.

9. Сохраните пакет. Тестовое приложение, которое создается далее, выполнит пакет и извлечет его выход непосредственно из памяти.

#### <a name="to-create-the-test-application"></a>Создание тестового приложения

1.  Создайте новое приложение Windows Forms.

2.  Добавьте ссылку на `Microsoft.SqlServer.Dts.DtsClient` пространство имен, перейдя к сборке с тем же именем в **%ProgramFiles%\Microsoft SQL Server\100\DTS\Binn**.

3.  Скопируйте и вставьте следующий образец кода в программный модуль формы.

4.  Измените значение `dtexecArgs` переменной в соответствии с требованиями, чтобы она содержала параметры командной строки, необходимые **dtexec.exe** для запуска пакета. В образце кода пакет загружается из файловой системы.

5.  Измените значение `dataReaderName` переменной в соответствии с требованиями, чтобы она содержала имя назначения DataReader в пакете.

6.  Поместите в форму кнопку и текстовое поле. В примере кода используется в `btnRun` качестве имени кнопки, а в `txtResults` качестве имени текстового поля.

7.  Запустите приложение и нажмите кнопку. После небольшой паузы, связанной с выполнением пакета, статистическое значение, вычисленное пакетом (количество клиентов в Канаде), должно отобразиться в текстовом поле формы.

### <a name="sample-code"></a>Пример кода

```vb
Imports System.Data
Imports Microsoft.SqlServer.Dts.DtsClient

Public Class Form1

  Private Sub btnRun_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles btnRun.Click

    Dim dtexecArgs As String
    Dim dataReaderName As String
    Dim countryName As String

    Dim dtsConnection As DtsConnection
    Dim dtsCommand As DtsCommand
    Dim dtsDataReader As IDataReader
    Dim dtsParameter As DtsDataParameter

    Windows.Forms.Cursor.Current = Cursors.WaitCursor

    dtexecArgs = "/FILE ""C:\...\DtsClientWParamPkg.dtsx"""
    dataReaderName = "DataReaderDest"
    countryName = "Canada"

    dtsConnection = New DtsConnection()
    With dtsConnection
      .ConnectionString = dtexecArgs
      .Open()
    End With

    dtsCommand = New DtsCommand(dtsConnection)
    dtsCommand.CommandText = dataReaderName

    dtsParameter = New DtsDataParameter("Country", DbType.String)
    dtsParameter.Direction = ParameterDirection.Input
    dtsCommand.Parameters.Add(dtsParameter)

    dtsParameter.Value = countryName

    dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default)

    With dtsDataReader
      .Read()
      txtResults.Text = .GetInt32(0).ToString("N0")
    End With

    'After reaching the end of data rows,
    ' call the Read method one more time.
    Try
      dtsDataReader.Read()
    Catch ex As Exception
      MessageBox.Show("Exception on final call to Read method:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception on final call to Read method", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    ' The following method is a best practice, and is
    '  required when using DtsDataParameter objects.
    dtsCommand.Dispose()

    Try
      dtsDataReader.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing DataReader:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing DataReader", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Try
      dtsConnection.Close()
    Catch ex As Exception
      MessageBox.Show("Exception closing connection:" & ControlChars.CrLf & _
      ex.Message & ControlChars.CrLf & _
      ex.InnerException.Message, "Exception closing connection", _
      MessageBoxButtons.OK, MessageBoxIcon.Error)
    End Try

    Windows.Forms.Cursor.Current = Cursors.Default

  End Sub

End Class
```

```csharp
using System;
using System.Windows.Forms;
using System.Data;
using Microsoft.SqlServer.Dts.DtsClient;

namespace DtsClientWParamCS
{
  public partial class Form1 : Form
  {
    public Form1()
    {
      InitializeComponent();
      this.btnRun.Click += new System.EventHandler(this.btnRun_Click);
    }

    private void btnRun_Click(object sender, EventArgs e)
    {
      string dtexecArgs;
      string dataReaderName;
      string countryName;

      DtsConnection dtsConnection;
      DtsCommand dtsCommand;
      IDataReader dtsDataReader;
      DtsDataParameter dtsParameter;

      Cursor.Current = Cursors.WaitCursor;

      dtexecArgs = @"/FILE ""C:\...\DtsClientWParamPkg.dtsx""";
      dataReaderName = "DataReaderDest";
      countryName = "Canada";

      dtsConnection = new DtsConnection();
      {
        dtsConnection.ConnectionString = dtexecArgs;
        dtsConnection.Open();
      }

      dtsCommand = new DtsCommand(dtsConnection);
      dtsCommand.CommandText = dataReaderName;

      dtsParameter = new DtsDataParameter("Country", DbType.String);
      dtsParameter.Direction = ParameterDirection.Input;
      dtsCommand.Parameters.Add(dtsParameter);

      dtsParameter.Value = countryName;

      dtsDataReader = dtsCommand.ExecuteReader(CommandBehavior.Default);

      {
        dtsDataReader.Read();
        txtResults.Text = dtsDataReader.GetInt32(0).ToString("N0");
      }

      //After reaching the end of data rows,
      // call the Read method one more time.
      try
      {
        dtsDataReader.Read();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception on final call to Read method:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception on final call to Read method", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      // The following method is a best practice, and is
      //  required when using DtsDataParameter objects.
      dtsCommand.Dispose();

      try
      {
        dtsDataReader.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing DataReader:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing DataReader", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      try
      {
        dtsConnection.Close();
      }
      catch (Exception ex)
      {
        MessageBox.Show(
          "Exception closing connection:\n" + ex.Message + "\n" + ex.InnerException.Message,
          "Exception closing connection", MessageBoxButtons.OK, MessageBoxIcon.Error);
      }

      Cursor.Current = Cursors.Default;

    }
  }
}
```

![Значок Integration Services (маленький)](../media/dts-16.gif "Значок служб Integration Services (маленький)")  **следит за обновлениями Integration Services**<br /> Чтобы загрузить новейшую документацию, статьи, образцы и видеоматериалы корпорации Майкрософт, а также лучшие решения участников сообщества, посетите страницу служб [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] на сайте MSDN:<br /><br /> [Посетить страницу «Службы Integration Services» на сайте MSDN](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Чтобы получать автоматические уведомления об этих обновлениях, подпишитесь на RSS-каналы, предлагаемые на этой странице.

## <a name="see-also"></a>См. также:
 [Основные сведения о различиях между локальной и удаленной](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) [загрузкой и запуском локального пакета](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) программным путем к программной [загрузке и запуску удаленного пакета](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)


