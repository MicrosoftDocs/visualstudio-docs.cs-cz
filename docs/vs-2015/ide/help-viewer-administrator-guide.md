---
title: Příručka správce Help Vieweru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f470c55b08cc559e481ed75e962fda4f0e625a5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871287"
---
# <a name="help-viewer-administrator-guide"></a>Příručka správce Help Vieweru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Help Viewer umožňuje spravovat místní instalace nápovědy pro síťové prostředí s nebo bez připojení k Internetu. Obsah místní nápovědy je konfigurován na jednotlivé počítače. Ve výchozím nastavení uživatelé musí mít práva správce k aktualizaci jejich místní instalace nápovědy.  
  
 Pokud vaše síťové prostředí umožňuje klientům přístup k Internetu, Help Viewer umožňuje nasadit místní obsah nápovědy z Internetu pomocí skriptů příkazového řádku.  
  
 Pokud vaše síťové prostředí neumožňuje klientům přístup k Internetu, Help Viewer umožňuje nasadit místní obsah nápovědy z intranetu nebo sdílené síťové složce. Můžete také zakázat možnosti nápovědy Visual Studio IDE, jako je například nápovědu online, offline, instalaci obsahu při prvním spuštění rozhraní IDE, určení obsahu služby intranetu a správu obsahu, pomocí přepisů klíče registru.  
  
 Základní syntaxe vypadá takto:  
  
 \<*Cesta k*> \HlpCtntmgr.exe /operation \< *argument*>/catalogname \< *název*>/locale \< *národníhoprostředí*>/sourceuri \< *cestu .msha nebo adresu URL*>  
  
 Další informace o syntaxi příkazového řádku HlpCtntMgr.exe naleznete v tématu [argumenty příkazového řádku pro Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Další informace o vytváření obsahu, vytváření koncového bodu služby intranetu a podobné typy aktivit najdete v Help Viewer SDK.  
  
## <a name="deploying-local-help-content-from-the-internet"></a>Nasazení obsahu místní nápovědy z Internetu  
 Obsah balíčku MSDN service můžete nasadit místní obsah nápovědy z Internetu do klientských počítačů. Použijte následující syntaxi:  
  
 \\<*Cesta k*> \v2.2\HlpCtntmgr.exe /operation \< *název*>/catalogname \< *název katalogu*>/locale \<  *národní prostředí*>  
  
 Další informace o syntaxi příkazového řádku HlpCtntMgr.exe naleznete v tématu [argumenty příkazového řádku pro Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).  
  
 Požadavky:  
  
- Klientské počítače musí mít přístup k Internetu.  
  
- Uživatelé musí mít práva správce k aktualizaci, přidání nebo odebrání místního obsahu nápovědy po jeho instalaci.  
  
  Upozornění:  
  
- Výchozí zdroj pro nápovědu bude stále Online.  
  
  > [!TIP]
  >  Výchozí zdroj pro nápovědu můžete změnit úpravou klíče registru HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Další informace najdete v tématu [správce obsahu nápovědy přepíše](../ide/help-content-manager-overrides.md).  
  
- Klienti se pořád výzva k instalaci základního obsahu nápovědy při prvním spuštění sady Visual Studio. Tuto výzvu můžete zakázat úpravou klíče registru HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.  
  
### <a name="example"></a>Příklad  
 Následující příklad instaluje obsah v angličtině pro sadu Visual Studio ke klientskému počítači.  
  
##### <a name="to-install-english-content-from-the-internet"></a>Instalace anglického obsahu z Internetu  
  
1.  Zvolte **Start** a klikněte na tlačítko **spustit**.  
  
2.  Zadejte následující příkaz:  
  
     C:\Program soubory (x86) \Microsoft Help Viewer\v2.2\hlpctntmgr.exe /operation instalace/catalogname VisualStudio14/Locale en-us  
  
3.  Stiskněte klávesu ENTER.  
  
## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Nasazení obsahu místní nápovědy předem nainstalovaných v klientských počítačích  
 Můžete nainstalovat sadu obsahu z online na jeden počítač a potom zkopírovat tuto nainstalovanou sadu obsahu do jiných počítačů.  
  
 Požadavky:  
  
- Na počítači, který nainstaluje sadu obsahu musí mít přístup k Internetu.  
  
- Uživatelé musí mít práva správce k aktualizaci, přidání nebo odebrání místního obsahu nápovědy po jeho instalaci.  
  
  > [!TIP]
  >  Pokud uživatelé nemají oprávnění správce, doporučujeme zakázat kartu spravovat obsah v Help Viewer. Další informace najdete v tématu [správce obsahu nápovědy přepíše](../ide/help-content-manager-overrides.md).  
  
  Upozornění:  
  
- Pokud uživatelé nemají oprávnění správce, doporučujeme zakázat kartu spravovat obsah v Help Viewer. Další informace najdete v tématu [správce obsahu nápovědy přepíše](../ide/help-content-manager-overrides.md).  
  
- Výchozí zdroj pro nápovědu bude stále Online.  
  
- Klienti se pořád výzva k instalaci základního obsahu nápovědy při prvním spuštění sady Visual Studio. Další informace najdete v tématu [správce obsahu nápovědy přepíše](../ide/help-content-manager-overrides.md).  
  
### <a name="create-the-content-set"></a>Vytvoření sady obsahu  
 Než budete moct vytvořit základní sadu obsahu, musíte nejprve odinstalovat veškerý místní obsah sady Visual Studio na cílovém počítači.  
  
##### <a name="to-uninstall-local-help"></a>Odinstalování místní nápovědy  
  
1. V okně Help Viewer zvolte **spravovat obsah** kartu.  
  
2. V části **dostupná dokumentace**, přejděte do sady dokumentů Visual Studio.  
  
3. Zvolte **odebrat** u každé podpoložky.  
  
4. Zvolte **Start** odinstalace  
  
5. Přejděte do *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 a ověřte, zda složka obsahuje pouze soubor catalogType.xml.  
  
   Jakmile jste odebrali všechny dříve nainstalované místní nápovědy aplikace Visual Studio obsah, jste připraveni stáhnout základní sadu obsahu.  
  
##### <a name="to-download-the-content"></a>Ke stažení obsahu  
  
1. V okně Help Viewer zvolte **spravovat obsah** kartu.  
  
2. V části **dostupná dokumentace**, přejděte do sad dokumentace, kterou chcete stáhnout a klikněte na tlačítko **přidat**.  
  
3. Zvolte **Start**.  
  
   Dále je třeba zabalit obsah balíčku, takže je možné nasadit do klientských počítačů.  
  
##### <a name="to-package-the-content"></a>Do balíčku obsahu  
  
1.  Vytvořte složku pro zkopírování obsahu pro pozdější nasazení.  
  
     Příklad: c:\VS12Help.  
  
2.  Otevřete cmd.exe s oprávněními správce.  
  
3.  Přejděte do složky, kterou jste vytvořili v kroku 1.  
  
4.  Zadejte následující příkaz:  
  
     Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \< *název_složky*> \ /y /e /k /o  
  
     Příklad: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`  
  
### <a name="deploying-the-content"></a>Nasazení obsahu  
  
##### <a name="to-deploy-the-content"></a>Nasazení obsahu  
  
1.  Vytvoření sdílené síťové složky a zkopírujte obsah nápovědy položku do tohoto umístění.  
  
     Například zkopírujte obsah v c:\VS12Help k \\\myserver\VS12Help.  
  
2.  Vytvořte soubor BAT obsahující skript nasazení pro obsah nápovědy. Vzhledem k tomu, klient může mít případně zámek pro čtení na kterýkoliv ze souborů, které jsou mazány jako součást nasdílení změn, měli byste vypnout před řízením aktualizací klienta.  
  
     Příklad:  
  
    ```  
    REM - copy pre-ripped content to ProgramData  
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o  
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to Programdata (%ERRORLEVEL%)  
  
    REM - get processor type and create/run registry update file  
    IF "%PROCESSOR_ARCHITECTURE%"=="AMD64" GOTO AMD64  
  
    @echo Architecture type is x86  
  
    ECHO Windows Registry Editor Version 5.00 > x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs] >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12] >> x86.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "FirstTimeRun"="False"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Help\v2.2\Catalogs\VisualStudio12\en-US]  >> x86.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\"  >> x86.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x86.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Microsoft\VSWinExpress\14.0\help]  >> x86.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x86.reg  
  
    regedit.exe /s x86.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x86 reg (%ERRORLEVEL%)  
  
    GOTO CONTINUE  
  
    :AMD64  
    @echo Architecture type is AMD64  
  
    ECHO Windows Registry Editor Version 5.00 > x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs] >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\" >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14] >> x64.reg  
    ECHO "LocationPath"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio14\\"  >> x64.reg  
    ECHO "FirstTimeRun"="False"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Help\v2.2\Catalogs\VisualStudio14\en-US]  >> x64.reg  
    ECHO "ContentStore"="%SYSTEMDRIVE%\\ProgramData\\Microsoft\\HelpLibrary2\\Catalogs\\VisualStudio12\\en-US\\"  >> x64.reg  
    ECHO "catalogName"="Visual Studio version Help Documentation"  >> x64.reg  
  
    ECHO [HKEY_LOCAL_MACHINE\Software\Wow6432Node\Microsoft\VSWinExpress\14.0\help]  >> x64.reg  
    ECHO "UseOnlineHelp"=dword:00000000  >> x64.reg  
  
    regedit.exe /s x64.reg  
    if ERRORLEVEL 1 ECHO *** ERROR inserting the x64 reg (%ERRORLEVEL%)  
  
    :CONTINUE  
    ```  
  
3.  Spusťte soubor bat v místních počítačích, které má být nainstalován na obsah nápovědy.  
  
## <a name="see-also"></a>Viz také  
 [Argumenty příkazového řádku pro Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md)   
 [Přepsání voleb Help Content Manageru](../ide/help-content-manager-overrides.md)



