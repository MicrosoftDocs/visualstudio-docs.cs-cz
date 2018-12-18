---
title: Příručka pro správce Prohlížeč nápovědy
ms.date: 11/01/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 4340c69f-b96b-4932-bb82-38b16a5ab149
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c58a0907f384c98ae3c1a341bc0e9be2794cdf18
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/13/2018
ms.locfileid: "53378185"
---
# <a name="help-viewer-administrator-guide"></a>Příručka pro správce Prohlížeč nápovědy

Aplikace Help Viewer umožňuje spravovat místní instalace nápovědy pro síťové prostředí s nebo bez připojení k Internetu. Obsah místní nápovědy je konfigurován na jednotlivé počítače. Ve výchozím nastavení uživatelé musí mít práva správce k aktualizaci jejich místní instalace nápovědy.

Pokud vaše síťové prostředí umožňuje klientům přístup k Internetu, můžete použít **aplikaci Help Content Manager** spustitelný nasadit místní obsah nápovědy z Internetu. Další informace o *HlpCtntMgr.exe* řádku syntaxe příkazu naleznete v tématu [argumenty příkazového řádku pro Help Content Manager](../help-viewer/command-line-arguments.md).

Informace o vytváření obsahu najdete v tématu Vytváření koncového bodu služby intranetu a podobné typy aktivit, [Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md).

Pokud vaše síťové prostředí nemají přístup k Internetu, Help Viewer umožňuje nasadit místní obsah nápovědy z intranetu nebo sdílené síťové složce. Můžete také zakázat možnosti nápovědy Visual Studio IDE pomocí [klíč registru přepíše](../help-viewer/behavior-overrides.md) pro funkce, jako například:

- online a offline nápovědu

- Instalace obsahu při prvním spuštění rozhraní IDE

- určení obsahu služby intranetu

- Správa obsahu

## <a name="deploy-local-help-content-from-the-internet"></a>Nasadit místní obsah nápovědy z Internetu

Můžete použít **aplikaci Help Content Manager** (*HlpCtntMgr.exe*) nasadit místní obsah nápovědy z Internetu do klientských počítačů. Použijte následující syntaxi:

```cmd
\\%ProgramFiles(x86)%\Microsoft Help Viewer\v2.3\HlpCtntmgr.exe /operation \<*name*> /catalogname \<*catalog name*> /locale \<*locale*>
```

Další informace o *HlpCtntMgr.exe* řádku syntaxe příkazu naleznete v tématu [argumenty příkazového řádku pro Help Content Manager](../help-viewer/command-line-arguments.md).

Požadavky:

-   Klientské počítače musí mít přístup k Internetu.

-   Uživatelé musí mít práva správce k aktualizaci, přidání nebo odebrání místního obsahu nápovědy po jeho instalaci.

Upozornění:

-   Výchozí zdroj pro nápovědu bude stále online.

### <a name="example"></a>Příklad

Následující příklad instaluje obsah v angličtině pro sadu Visual Studio ke klientskému počítači.

#### <a name="to-install-english-content-from-the-internet"></a>Instalace anglického obsahu z Internetu

1.  Zvolte **Start** a klikněte na tlačítko **spustit**.

2.  Zadejte následující příkaz:

     `C:\Program Files (x86)\Microsoft Help Viewer\v2.3\hlpctntmgr.exe /operation install /catalogname VisualStudio15 /locale en-us`

3.  Stisknutím klávesy **zadejte**.

## <a name="deploy-pre-installed-local-help-content-on-client-computers"></a>Nasadit předem nainstalované místní obsah nápovědy v klientských počítačích

Můžete nainstalovat sadu obsahu z online na jeden počítač a potom zkopírovat tuto nainstalovanou sadu obsahu do jiných počítačů.

Požadavky:

-   Na počítači, který nainstaluje sadu obsahu musí mít přístup k Internetu.

-   Uživatelé musí mít práva správce k aktualizaci, přidání nebo odebrání místního obsahu nápovědy po jeho instalaci.

    > [!TIP]
    > Pokud uživatelé nemají oprávnění správce, doporučuje se, že zakážete **spravovat obsah** kartě v aplikaci Help Viewer. Další informace najdete v tématu [aplikaci Help Content Manager přepíše](../help-viewer/behavior-overrides.md).

Upozornění:

-   Výchozí zdroj pro nápovědu bude stále online.

### <a name="create-the-content-set"></a>Vytvoření sady obsahu

Než budete moct vytvořit základní sadu obsahu, musíte nejprve odinstalovat veškerý místní obsah sady Visual Studio na cílovém počítači.

#### <a name="to-uninstall-local-help"></a>Odinstalování místní nápovědy

1. V okně Help Viewer zvolte **spravovat obsah** kartu.

2. Přejděte do sady dokumentů Visual Studio.

3. Zvolte **odebrat** u každé podpoložky.

4. Zvolte **aktualizace** odinstalovat.

5. Přejděte do *%ProgramData%\Microsoft\HelpLibrary2\Catalogs\VisualStudio15* a ověřte, zda složka obsahuje pouze soubor *catalogType.xml*.

   Jakmile jste odebrali všechny dříve nainstalované místní nápovědy aplikace Visual Studio obsah, jste připraveni stáhnout základní sadu obsahu.

#### <a name="to-download-the-content"></a>Ke stažení obsahu

1.  V okně Help Viewer zvolte **spravovat obsah** kartu.

2.  V části **doporučená dokumentace** nebo **dostupná dokumentace**, přejděte do sad dokumentace, kterou chcete stáhnout a klikněte na tlačítko **přidat**.

3.  Zvolte **aktualizace**.

Dále je třeba zabalit obsah balíčku, takže je možné nasadit do klientských počítačů.

#### <a name="to-package-the-content"></a>Do balíčku obsahu

1.  Vytvořte složku pro zkopírování obsahu pro pozdější nasazení. Příklad: *C:\VSHelp*.

2.  Otevřít *cmd.exe* s oprávněními správce.

3.  Přejděte do složky, kterou jste vytvořili v kroku 1.

4.  Zadejte následující příkaz:

     `Xcopy %ProgramData%\Microsoft\HelpLibrary2 \<*foldername*>\ /y /e /k /o `

     Příklad: `Xcopy %ProgramData%\Microsoft\HelpLibrary2 c:\VSHelp\ /y /e /k /o`

### <a name="deploy-the-content"></a>Nasazení obsahu

1.  Vytvoření sdílené síťové složky a zkopírujte obsah nápovědy do daného umístění.

     Například zkopírujte obsah *C:\VSHelp* k  *\\\myserver\VSHelp*.

2.  Vytvoření *.bat* soubor obsahující skript nasazení pro obsah nápovědy. Vzhledem k tomu, klient může mít případně zámek pro čtení na kterýkoliv ze souborů, které jsou mazány jako součást nasdílení změn, měli byste vypnout před řízením aktualizací klienta. Příklad:

    ```cmd
    REM - copy pre-ripped content to ProgramData
    Xcopy %~dp0HelpLibrary2 %SYSTEMDRIVE%\ProgramData\Microsoft\HelpLibrary2\ /y /e /k /o
    if ERRORLEVEL 1 ECHO *** ERROR COPYING Help Library files to ProgramData (%ERRORLEVEL%)
    ```

3.  Spustit *.bat* soubor v místních počítačích, které chcete nainstalovat obsah nápovědy.

## <a name="see-also"></a>Viz také:

- [Argumenty příkazového řádku pro Help Content Manager](../help-viewer/command-line-arguments.md)
- [Přepíše Help Content Manager](../help-viewer/behavior-overrides.md)
- [Microsoft Help Viewer 2.2](../help-viewer/overview.md)
- [Aplikaci Help Viewer SDK](../extensibility/internals/microsoft-help-viewer-sdk.md)