---
title: Ladění rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio | Microsoft Docs
description: Rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio. Ladění rozšíření nástrojů služby SharePoint v experimentální instanci nebo v normální instanci VS.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 2b098ac007825745e13481592760be9d2badeb55
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948905"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio
  Rozšíření nástrojů služby SharePoint můžete ladit v experimentální instanci nebo v běžné instanci aplikace Visual Studio. Pokud potřebujete řešit potíže s chováním rozšíření, můžete také změnit hodnoty registru a zobrazit tak další informace o chybě a nakonfigurovat, jak aplikace Visual Studio provede příkazy služby SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Rozšíření ladění v experimentální instanci sady Visual Studio
 Chcete-li chránit vývojové prostředí sady Visual Studio před náhodným poškozením netestovanými rozšířeními, sada Visual Studio SDK poskytuje alternativní instanci sady Visual Studio, která se nazývá *experimentální instance*, kterou můžete použít k instalaci a testování rozšíření. Vyvíjíte nová rozšíření pomocí běžné instance sady Visual Studio, ale ladíte a spouštíte je v experimentální instanci. Další informace najdete v [experimentální instanci](../extensibility/the-experimental-instance.md).

 Použijete-li k nasazení rozšíření projekt VSIX a projekt VSIX je projekt po spuštění ve vašem řešení, Visual Studio automaticky nainstaluje a spustí rozšíření v experimentální instanci při ladění řešení. Spouštěný projekt je projekt, který se spustí při ladění řešení, které obsahuje více projektů. Další informace o použití projektu VSIX k nasazení rozšíření naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Příklady, které ukazují, jak ladit různé typy rozšíření v experimentální instanci aplikace Visual Studio, naleznete v následujících návodech:

- [Návod: rozšiřování typu položky projektu služby SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

- [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

- [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

- [Návod: volání do objektového modelu klienta služby SharePoint v rozšíření Průzkumník serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Rozšíření ladění v normální instanci sady Visual Studio
 Pokud chcete ladit projekt rozšíření v normální instanci aplikace Visual Studio, nejprve nainstalujte rozšíření v normální instanci. Pak připojte ladicí program k druhému procesu sady Visual Studio. Po dokončení můžete rozšíření odebrat, aby se už nenačítal do vývojového počítače.

#### <a name="to-install-the-extension"></a>Instalace rozšíření

1. Zavřete všechny instance aplikace Visual Studio.

2. Ve výstupní složce sestavení pro projekt rozšíření otevřete soubor *. vsix* poklikáním nebo otevřením jeho místní nabídky a následným výběrem možnosti **otevřít**:

3. V dialogovém okně **instalační program rozšíření sady Visual Studio** zvolte edici sady Visual Studio, do které chcete rozšíření nainstalovat, a poté klikněte na tlačítko **instalovat** .

     Visual Studio nainstaluje soubory rozšíření do%USERPROFILE%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions \\  \\ *názvu přípony* názvu autora \\ . Poslední tři složky v této cestě jsou sestaveny z `Author` prvků, `Name` a `Version` v souboru *extension. vsixmanifest* pro rozšíření.

4. Poté, co Visual Studio nainstaluje rozšíření, klikněte na tlačítko **Zavřít** .

#### <a name="to-debug-the-extension"></a>Ladění rozšíření

1. Otevřete Visual Studio s oprávněními správce a otevřete projekt rozšíření. Následující kroky odkazují na tuto instanci aplikace Visual Studio jako na *první instanci*.

2. Spusťte jinou instanci aplikace Visual Studio s oprávněními správce. Následující kroky odkazují na tuto instanci aplikace Visual Studio jako na *druhou instanci*.

3. Přepněte na první instanci sady Visual Studio.

4. Na řádku nabídek klikněte na položku **ladit**, **připojit k procesu**.

5. V seznamu **procesy k dispozici** vyberte možnost *devenv.exe*. Tato položka odkazuje na druhou instanci aplikace Visual Studio; Toto je instance, ve které chcete ladit rozšíření projektu.

6. Klikněte na tlačítko **připojit** .

     Visual Studio spustí projekt rozšíření v režimu ladění.

7. Přepněte na druhou instanci aplikace Visual Studio.

8. Vytvořte nový projekt služby SharePoint, který načte vaše rozšíření. Například pokud ladíte rozšíření pro položky projektu definice seznamu, vytvořte projekt **definice seznamu** .

9. K otestování kódu rozšíření je nutné provést libovolné kroky.

10. Po dokončení ladění rozšíření Zavřete druhou instanci aplikace Visual Studio.

#### <a name="to-remove-the-extension"></a>Odebrání rozšíření

1. V aplikaci Visual Studio na řádku nabídek vyberte **nástroje**, **rozšíření a aktualizace**.

     Otevře se dialogové okno **rozšíření a aktualizace** .

2. V seznamu rozšíření zvolte název rozšíření a pak klikněte na tlačítko **odinstalovat** .

3. V dialogovém okně, které se zobrazí, klikněte na tlačítko **Ano** a potvrďte tak, že chcete rozšíření odinstalovat.

4. Kliknutím na tlačítko **restartovat nyní** dokončete odinstalaci.

## <a name="debug-sharepoint-commands"></a>Ladění příkazů služby SharePoint
 Chcete-li ladit příkaz služby SharePoint, který je součástí rozšíření nástrojů služby SharePoint, je nutné připojit ladicí program k procesu *vssphost4.exe* . Toto je 64 hostitelský proces, který spouští příkazy služby SharePoint. Další informace o příkazech a *vssphost4.exeech* služby SharePoint naleznete v tématu [Calling to a model Object Models služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Připojení ladicího programu k procesu vssphost4.exe

1. Spusťte ladění rozšíření v experimentální instanci aplikace Visual Studio nebo normální instanci sady Visual Studio podle pokynů uvedených výše.

2. V instanci aplikace Visual Studio, ve které je spuštěn ladicí program, vyberte v řádku nabídek možnost **ladit**, **připojit k procesu**.

3. V seznamu **procesy k dispozici** vyberte možnost *vssphost.exe*.

    > [!NOTE]
    > Pokud se vssphost.exe v seznamu nezobrazí, je nutné spustit proces *vssphost4.exe* v instanci aplikace Visual Studio, ve které je rozšíření spuštěno. Obvykle to provedete provedením akce, která způsobí, že se Visual Studio připojí k webu služby SharePoint ve vývojovém počítači. Například Visual Studio se spustí *vssphost4.exe* , když rozbalíte uzel připojení lokality (uzel, který zobrazuje adresu URL webu) v uzlu **připojení služby sharepoint** v okně **Průzkumník serveru** nebo když do projektu služby SharePoint přidáte určité položky projektu služby SharePoint, jako je například **instance seznamu** nebo položky **přijímače událostí** .

4. Klikněte na tlačítko **připojit** .

5. V instanci aplikace Visual Studio, která je laděna, proveďte kroky, které jsou nutné ke spuštění příkazu.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Úprava hodnot registru pro usnadnění ladění rozšíření nástrojů služby SharePoint
 Když ladíte rozšíření nástrojů služby SharePoint v aplikaci Visual Studio, můžete upravit hodnoty v registru, které vám pomohou s tímto rozšířením. Hodnoty existují pod klíčem **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** . Tyto hodnoty ve výchozím nastavení neexistují.

 Chcete-li pomoct řešit jakékoli rozšíření nástrojů služby SharePoint, můžete vytvořit a nastavit hodnotu EnableDiagnostics. Tato hodnota je popsána v následující tabulce.

|Hodnota|Popis|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, která určuje, zda jsou diagnostické zprávy zobrazeny v okně **výstup** .<br /><br /> Chcete-li zobrazit diagnostické zprávy, nastavte tuto hodnotu na 1. Chcete-li ukončit zobrazování zpráv, nastavte tuto hodnotu na 0 nebo tuto hodnotu odstraňte.<br /><br /> Chcete-li zapsat zprávy do okna **výstup** z rozšíření nástrojů služby SharePoint, použijte službu projektu SharePoint. Další informace naleznete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Pokud vaše rozšíření obsahuje příkaz SharePoint, můžete vytvořit a nastavit další hodnoty, které vám pomohou při odstraňování potíží s příkazem. Tyto hodnoty jsou popsány v následující tabulce.

|Hodnota|Popis|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, která určuje, zda se má zobrazit dialogové okno, které umožňuje připojit ladicí program k *vssphost4.exe* ihned po spuštění. To je užitečné, pokud příkaz, který chcete ladit, je spuštěn vssphost.exe hned po jeho spuštění a není dostatek času k ručnímu připojení ladicího programu před provedením příkazu. Chcete-li zobrazit dialogové okno, *vssphost4.exe* volá <xref:System.Diagnostics.Debugger.Break%2A> metodu při spuštění.<br /><br /> Chcete-li toto chování povolit, nastavte tuto hodnotu na 1. Chcete-li toto chování vypnout, nastavte tuto hodnotu na 0 nebo tuto hodnotu odstraňte.<br /><br /> Pokud nastavíte tuto hodnotu na 1, můžete také zvýšit hodnotu HostProcessStartupTimeout a poskytnout tak dostatek času na připojení ladicího programu, než sada Visual Studio *vssphost4.exe* očekává, že se úspěšně spustila.|
|ChannelOperationTimeout|REG_DWORD, která určuje čas (v sekundách), po který Visual Studio čeká na provedení příkazu SharePointu. Pokud se příkaz nespustí v čase, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> je vyvolána výjimka.<br /><br /> Výchozí hodnota je 120 sekund.|
|HostProcessStartupTimeout|REG_DWORD, která určuje čas (v sekundách), po který Visual Studio počká, než *vssphost4.exe* signál, že byl úspěšně spuštěn. Pokud *vssphost4.exe* nesignalizuje úspěšné spuštění v čase, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> je vyvolána výjimka.<br /><br /> Výchozí hodnota je 60 sekund.|
|MaxReceivedMessageSize|REG_DWORD, které určuje maximální povolenou velikost v bajtech zpráv WCF, které jsou předány mezi Visual Studio a *vssphost4.exe*.<br /><br /> Výchozí hodnota je 1 048 576 bajtů (1 MB).|
|MaxStringContentLength|REG_DWORD, která určuje maximální povolenou velikost v bajtech pro řetězce, které jsou předávány mezi Visual Studio a *vssphost4.exe*.<br /><br /> Výchozí hodnota je 1 048 576 bajtů (1 MB).|

## <a name="see-also"></a>Viz také

- [Rozšiřování nástrojů služby SharePoint v aplikaci Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
