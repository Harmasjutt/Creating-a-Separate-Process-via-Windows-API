# Creating-a-Separate-Process-via-Windows-API
#include<stdio.h>
#include<windows.h>
int main(VOID)
{
STARTUPINFO si;
PROCESS_INFORMATION pi;
ZeroMemory(&pi, sizeof(pi));
if(!CreateProcess(NULL,"C:\\WINDOWS\\system32\\mspaint.exe", NULL, NULL, FALSE, 0, NULL, NULL, &si, &pi))
{
fprintf(stderr, "create process Failed");
return -1;
}
WaitForSingleObject(pi.hProcess, INFINITE);
printf("child complete");
CloseHandle(pi.hProcess);
CloseHandle(pi.hThread);
}
