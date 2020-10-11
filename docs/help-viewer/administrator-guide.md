---
title: Příručka pro správce prohlížeče nápovědy
description: Přečtěte si příručku pro správce Microsoft Help Viewer. Nasaďte místní obsah z Internetu nebo nasaďte předem nainstalovaný obsah místní aplikace v klientských počítačích.
ms.date: 11/01/2017
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 312b886ee0becc794f657ecaaba7fb028d4b3cf1
ms.sourcegitcommit: dfbbf041e68ec3a4cd97196b19c9226a4793e702
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2020
ms.locfileid: "91878888"
---
# <a name="help-viewer-administrator-guide"></a>Příručka pro správce prohlížeče nápovědy

Aplikace Help Viewer umožňuje spravovat místní instalace nápovědy pro síťová prostředí s přístupem k Internetu nebo bez něj. Místní obsah obsahu Help je nakonfigurován pro jednotlivé počítače zvlášť. Ve výchozím nastavení musí mít uživatelé oprávnění správce, aby mohli aktualizovat místní instalaci aplikace Help.

Pokud vaše síťové prostředí umožňuje klientům přístup k Internetu, můžete pomocí spustitelného souboru aplikace **help Content Manager** nasadit místní obsah z Internetu. Další informace o *HlpCtntMgr.exe* syntaxi příkazového řádku najdete v tématu [argumenty příkazového řádku pro nástroj Help Content Manager](../help-viewer/command-line-arguments.md).

Informace o vytváření obsahu, vytváření koncového bodu služby v intranetu a podobných typech aktivit najdete v tématu [sada Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Pokud ve svém síťovém prostředí nemáte přístup k Internetu, může aplikace Help Viewer nasadit místní obsah nápovědy z intranetu nebo ze sdílené síťové složky. Možnosti pomoci s prostředím IDE sady Visual Studio můžete také zakázat pomocí [přepsání klíčů registru](../help-viewer/behavior-overrides.md) pro funkce, jako například:

- online pomocník proti offline práci

- Instalace obsahu při prvním spuštění rozhraní IDE

- určení služby obsahu v intranetu

- Správa obsahu

## <a name="deploy-local-help-content-from-the-internet"></a>Nasadit místní obsah v nápovědě z Internetu

**Nástroj Help Content Manager** (*HlpCtntMgr.exe*) můžete použít k nasazení místního obsahu aplikace z Internetu do klientských počítačů. Použijte následující syntaxi:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Další informace o *HlpCtntMgr.exe* syntaxi příkazového řádku najdete v tématu [argumenty příkazového řádku pro nástroj Help Content Manager](../help-viewer/command-line-arguments.md).

Požadavky:

- Klientské počítače musí mít přístup k Internetu.

- Uživatelé musí mít oprávnění správce, aby mohli aktualizovat, přidat nebo odebrat místní obsah v nápovědě po jeho instalaci.

Upozornění

- Výchozí zdroj pro nápovědu bude stále online.

### <a name="example"></a>Příklad

Následující příklad nainstaluje obsah v angličtině pro Visual Studio do klientského počítače.

#### <a name="to-install-english-content-from-the-internet"></a>Instalace anglického obsahu z Internetu

1. Zvolte **Start** a pak zvolte **Spustit**.

2. Zadejte:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Stiskněte **Enter**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Nasazení předem nainstalovaného obsahu místní verze Help na klientských počítačích

Můžete nainstalovat sadu obsahu z online do jednoho počítače a potom zkopírovat nainstalovanou sadu obsahu do jiných počítačů.

Požadavky:

- Počítač, do kterého instalujete sadu obsahu, musí mít přístup k Internetu.

- Uživatelé musí mít oprávnění správce, aby mohli aktualizovat, přidat nebo odebrat místní obsah v nápovědě po jeho instalaci.

    > [!TIP]
    > Pokud uživatelé nemají práva správce, doporučujeme zakázat kartu **Spravovat obsah** v programu Help Viewer. Další informace najdete v tématu [potlačení aplikace Help Content Manager](../help-viewer/behavior-overrides.md).

Upozornění

- Výchozí zdroj pro nápovědu bude stále online.

### <a name="create-the-content-set"></a>Vytvořit sadu obsahu

Než budete moct vytvořit základní sadu obsahu, musíte nejdřív odinstalovat veškerý místní obsah sady Visual Studio na cílovém počítači.

#### <a name="to-uninstall-local-help"></a>Odinstalace místní Help

1. V programu Help Viewer klikněte na kartu **Spravovat obsah** .

2. Přejděte do sady dokumentů sady Visual Studio.

3. Vyberte možnost **Odebrat** vedle každé dílčí položky.

4. Pro odinstalaci vyberte **aktualizovat** .

5. Přejděte na *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* a ověřte, zda složka obsahuje pouze soubor *catalogType.xml*.

   Po odebrání veškerého dříve nainstalovaného obsahu místní aplikace sady Visual Studio budete připraveni stáhnout základní sadu obsahu.

#### <a name="to-download-the-content"></a>Stažení obsahu

1. V programu Help Viewer klikněte na kartu **Spravovat obsah** .

2. V části **doporučená dokumentace** nebo **dostupná dokumentace**přejděte do sady dokumentace, které chcete stáhnout, a pak zvolte **Přidat**.

3. Vyberte **aktualizovat**.

Dále je nutné zabalit obsah, aby jej bylo možné nasadit do klientských počítačů.

#### <a name="to-package-the-content"></a>Balení obsahu

1. Vytvořte složku, do které se má obsah zkopírovat pro pozdější nasazení. Například: *C:\VSHelp*.

2. Otevřete *cmd.exe* s oprávněními správce.

3. Přejděte do složky, kterou jste vytvořili v kroku 1.

4. Zadejte:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o`

     Příklad: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Nasazení obsahu

1. Vytvořte sdílenou síťovou složku a zkopírujte obsah vaší aplikace do tohoto umístění.

     Zkopírujte například obsah v *C:\VSHelp* do * \\ \myserver\VSHelp*.

2. Vytvořte soubor *. bat* , který bude obsahovat skript nasazení pro obsah aplikace Help. Vzhledem k tomu, že klient může mít zámek proti čtení u některého ze souborů, které se odstraňují jako součást nabízené instalace, měli byste klienta před vložením aktualizací vypnout. Například:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3. Spusťte soubor *. bat* na místních počítačích, do kterých chcete nainstalovat obsah této části.

## <a name="see-also"></a>Viz také

- [Argumenty příkazového řádku pro správce obsahu pro nápovědu](../help-viewer/command-line-arguments.md)
- [Přepsání v nápovědě pro Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
- [Sada Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)