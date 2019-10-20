---
title: Příručka pro správce Help Vieweru | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-help-viewer
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 03cacd8de574de92002b44b237cd84c22e761eaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72645578"
---
# <a name="help-viewer-administrator-guide"></a>Příručka správce Help Vieweru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aplikace Help Viewer umožňuje spravovat místní instalace nápovědy pro síťová prostředí s přístupem k Internetu nebo bez něj. Místní obsah obsahu Help je nakonfigurován pro jednotlivé počítače zvlášť. Ve výchozím nastavení musí mít uživatelé oprávnění správce, aby mohli aktualizovat místní instalaci aplikace Help.

 Pokud vaše síťové prostředí umožňuje klientům přístup k Internetu, aplikace Help Viewer umožňuje použít skripty příkazového řádku k nasazení místního obsahu nápovědy z Internetu.

 Pokud vaše síťové prostředí neumožňuje klientům přístup k Internetu, může aplikace Help Viewer nasadit místní obsah nápovědy z intranetu nebo ze sdílené síťové složky. Můžete také zakázat možnosti pomocníka s prostředím IDE sady Visual Studio, jako je online nebo offline, instalace obsahu při prvním spuštění rozhraní IDE, určení služby obsahu v intranetu a Správa obsahu pomocí přepsání klíče registru.

 Základní syntaxe je následující:

 \<*cesta k*> \HlpCtntmgr.exe/Operation \<*argument*>/CatalogName \<*název*> povinný/locale. \<*locale*>/sourceuri \< *. msha cesta nebo adresa URL* 0

 Další informace o syntaxi příkazového řádku HlpCtntMgr. exe najdete v tématu [argumenty příkazového řádku pro nástroj Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).

 Další informace o vytváření obsahu, vytváření koncového bodu služby v intranetu a podobných typech aktivit najdete v tématu sada Help Viewer SDK.

## <a name="deploying-local-help-content-from-the-internet"></a>Nasazování obsahu místní aplikace z Internetu
 Pomocí služby balíčku obsahu MSDN můžete nasadit místní obsah aplikace z Internetu do klientských počítačů. Použijte následující syntaxi:

 \\ <*cesta k*> \v2.2\HlpCtntmgr.exe/Operation \<*název*>/CatalogName \<*katalogu*> povinný/locale. \<*locale* >

 Další informace o syntaxi příkazového řádku HlpCtntMgr. exe najdete v tématu [argumenty příkazového řádku pro nástroj Help Content Manager](../ide/command-line-arguments-for-the-help-content-manager.md).

 Požadavků

- Klientské počítače musí mít přístup k Internetu.

- Uživatelé musí mít oprávnění správce, aby mohli aktualizovat, přidat nebo odebrat místní obsah v nápovědě po jeho instalaci.

  Upozornění

- Výchozí zdroj pro nápovědu bude stále online.

  > [!TIP]
  > Výchozí zdroj pro nápovědu můžete změnit úpravou klíče registru HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\14.0\help\UseOnlineHelp. Další informace najdete v tématu [potlačení aplikace Help Content Manager](../ide/help-content-manager-overrides.md).

- Klienti budou stále vyzváni k instalaci základního obsahu v nápovědě při prvním spuštění sady Visual Studio. Tuto výzvu můžete zakázat úpravou klíče registru HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\VisualStudio\14.0\Help\DisableFirstRunHelpSelection.

### <a name="example"></a>Příklad
 Následující příklad nainstaluje obsah v angličtině pro Visual Studio do klientského počítače.

##### <a name="to-install-english-content-from-the-internet"></a>Instalace anglického obsahu z Internetu

1. Zvolte **Start** a pak zvolte **Spustit**.

2. Zadejte následující:

     C:\Program Files (x86) \Microsoft Help Viewer\v2.2\HlpCtntmgr.exe/Operation Install/CatalogName VisualStudio14 povinný/locale. en-US

3. Stiskněte klávesu ENTER.

## <a name="deploying-pre-installed-local-help-content-on-client-computers"></a>Nasazení předem nainstalovaného obsahu místní verze Help na klientských počítačích
 Můžete nainstalovat sadu obsahu z online do jednoho počítače a potom zkopírovat nainstalovanou sadu obsahu do jiných počítačů.

 Požadavků

- Počítač, do kterého instalujete sadu obsahu, musí mít přístup k Internetu.

- Uživatelé musí mít oprávnění správce, aby mohli aktualizovat, přidat nebo odebrat místní obsah v nápovědě po jeho instalaci.

  > [!TIP]
  > Pokud uživatelé nemají práva správce, doporučujeme zakázat kartu spravovat obsah v programu Help Viewer. Další informace najdete v tématu [potlačení aplikace Help Content Manager](../ide/help-content-manager-overrides.md).

  Upozornění

- Pokud uživatelé nemají práva správce, doporučujeme zakázat kartu spravovat obsah v programu Help Viewer. Další informace najdete v tématu [potlačení aplikace Help Content Manager](../ide/help-content-manager-overrides.md).

- Výchozí zdroj pro nápovědu bude stále online.

- Klienti budou stále vyzváni k instalaci základního obsahu v nápovědě při prvním spuštění sady Visual Studio. Další informace najdete v tématu [potlačení aplikace Help Content Manager](../ide/help-content-manager-overrides.md).

### <a name="create-the-content-set"></a>Vytvořit sadu obsahu
 Než budete moct vytvořit základní sadu obsahu, musíte nejdřív odinstalovat veškerý místní obsah sady Visual Studio na cílovém počítači.

##### <a name="to-uninstall-local-help"></a>Odinstalace místní Help

1. V programu Help Viewer klikněte na kartu **Spravovat obsah** .

2. V části **dostupná dokumentace**přejděte do sady Visual Studio sada dokumentů.

3. Vyberte možnost **Odebrat** vedle každé dílčí položky.

4. Zvolit možnost **Spustit** pro odinstalaci

5. Přejděte na *n*: \ProgramData\Microsoft\HelpLibrary2\Catalogs\VisualStudio12 a ověřte, zda složka obsahuje pouze soubor catalogType. XML.

   Po odebrání veškerého dříve nainstalovaného obsahu místní aplikace sady Visual Studio budete připraveni stáhnout základní sadu obsahu.

##### <a name="to-download-the-content"></a>Stažení obsahu

1. V programu Help Viewer klikněte na kartu **Spravovat obsah** .

2. V části **dostupná dokumentace**přejděte do sady dokumentace, které chcete stáhnout, a pak zvolte **Přidat**.

3. Klikněte na tlačítko **Spustit**.

   Dále je nutné zabalit obsah, aby jej bylo možné nasadit do klientských počítačů.

##### <a name="to-package-the-content"></a>Balení obsahu

1. Vytvořte složku, do které se má obsah zkopírovat pro pozdější nasazení.

     Příklad: c:\VS12Help.

2. Otevřete cmd. exe s oprávněními správce.

3. Přejděte do složky, kterou jste vytvořili v kroku 1.

4. Zadejte následující:

     Xcopy%SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 \<*název_složky*> \/y/e/k/o

     Příklad: `Xcopy %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2 c:\VS12Help\ /y /e /k /o`

### <a name="deploying-the-content"></a>Nasazení obsahu

##### <a name="to-deploy-the-content"></a>Nasazení obsahu

1. Vytvořte sdílenou síťovou složku a zkopírujte obsah aplikace příponou do tohoto umístění.

     Například zkopírujte obsah v c:\VS12Help do \\ \myserver\VS12Help.

2. Vytvořte soubor. bat, který bude obsahovat skript nasazení pro obsah aplikace Help. Vzhledem k tomu, že klient může mít zámek proti čtení u některého ze souborů, které se odstraňují jako součást nabízené instalace, měli byste klienta před vložením aktualizací vypnout.

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

3. Spusťte soubor bat na místních počítačích, do kterých má být nainstalován obsah pro podporu.

## <a name="see-also"></a>Viz také
 [Argumenty příkazového řádku pro](../ide/command-line-arguments-for-the-help-content-manager.md) [Správce obsahu](../ide/help-content-manager-overrides.md) Help Content Manageru přepsání
