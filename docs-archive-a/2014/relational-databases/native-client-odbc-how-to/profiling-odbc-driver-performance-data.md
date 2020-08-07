---
title: Данные производительности драйвера профиля (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: rothja
ms.author: jroth
ms.openlocfilehash: 3575cfd304d526bdb25eee6a2578d67c6bb67bc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730649"
---
# <a name="profile-driver-performance-data-odbc"></a>Сбор сведений о производительности драйвера (ODBC)
  В этом образце показаны параметры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для драйвера ODBC, относящиеся к сбору статистики производительности. Образец создает один файл: odbcperf.log. Этот образец показывает и создание файла журнала со сведениями о производительности, и отображение сведений о производительности непосредственно из структуры данных SQLPERF (структура SQLPERF определена в файле Odbcss.h.). Этот образец разработан для ODBC версии 3.0 или более поздней.  
  
> [!IMPORTANT]  
>  По возможности используйте аутентификацию Windows. Если проверка подлинности Windows недоступна, запросите у пользователя ввод учетных данных во время выполнения. Избегайте хранения учетных данных в файле. Если необходимо сохранить учетные данные, зашифруйте их с помощью [API-интерфейса шифрования Win32](https://go.microsoft.com/fwlink/?LinkId=64532).  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a>Запись сведений о производительности драйвера при помощи администратора ODBC  
  
1.  На **панели управления**дважды щелкните **Администрирование** , а затем дважды щелкните **Источники данных (ODBC)**. Можно также вызвать программу odbcad32.exe.  
  
2.  Щелкните вкладку **DSN пользователя**, **системное имя DSN**или **Файловый DSN** .  
  
3.  Щелкните источник данных, для которого необходимо заносить в журнал производительность.  
  
4.  Щелкните **Настройка**.  
  
5.  В мастере настройки имени DSN Microsoft SQL Server перейдите к странице с **записью статистики драйвера ODBC log в файл журнала**.  
  
6.  Выберите **Журнал статистика драйвера ODBC в файле журнала**. В поле укажите имя файла, куда будет записана статистика. При необходимости нажмите кнопку **Обзор** , чтобы просмотреть файловую систему для журнала статистики.  
  
### <a name="to-log-driver-performance-data-programmatically"></a>Программная запись сведений о производительности драйвера  
  
1.  Вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA_LOG, а также полный путь и имя файла журнала данных производительности. Пример:  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  Вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_START, чтобы начать запись данных о производительности.  
  
3.  При необходимости вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_LOG_NOW и NULL, чтобы записать в файл журнала данных производительности записи с разделителями-символами табуляции. Это можно делать каждый раз при запуске приложения.  
  
4.  Вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_STOP, чтобы отключить ведение журнала данных о производительности.  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a>Получение в приложение данных о производительности  
  
1.  Вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_START, чтобы начать профилирование данных производительности.  
  
2.  Вызовите [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) с SQL_COPT_SS_PERF_DATA и адресом указателя на структуру SQLPERF. Первый такой вызов установит указатель на адрес допустимой структуры SQLPERF, содержащей текущие сведения о производительности. Драйвер не обновляет непрерывно данные в структуре производительности. Приложение должно повторить вызов [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) каждый раз, когда ему потребуется обновить структуру с более актуальными данными о производительности.  
  
3.  Вызовите [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) с SQL_COPT_SS_PERF_DATA и SQL_PERF_STOP, чтобы отключить ведение журнала данных о производительности.  
  
## <a name="example"></a>Пример  
 Также необходим источник данных ODBC с именем AdventureWorks, для которого базой данных по умолчанию является образец базы данных AdventureWorks. (Образец базы данных AdventureWorks можно скачать на домашней странице [Microsoft SQL Server примеры и проекты сообщества](https://go.microsoft.com/fwlink/?LinkID=85384) .) Этот источник данных должен быть основан на драйвере ODBC, предоставленном операционной системой (имя драйвера — "SQL Server"). При построении и запуске этого образца как 32-разрядного приложения в 64-разрядной операционной системе необходимо создать источник данных ODBC с помощью программы администрирования ODBC (исполняемый файл %windir%\SysWOW64\odbcad32.exe).  
  
 Этот образец соединяется с установленным на компьютер экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] по умолчанию. Чтобы соединиться с именованным экземпляром, измените определение источника данных ODBC, указав экземпляр в следующем формате: Сервер\ИменованныйЭкземпляр. По умолчанию [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] устанавливается на именованный экземпляр.  
  
 Скомпилируйте с библиотекой odbc32.lib.  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a>См. также:  
 [Инструкции по профилированию производительности драйвера ODBC &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md)   
 [Создание профилей производительности драйвера ODBC](../native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
