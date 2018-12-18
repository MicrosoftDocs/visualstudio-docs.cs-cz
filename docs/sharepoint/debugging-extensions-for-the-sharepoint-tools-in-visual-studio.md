---
title: Ladění rozšíření pro nástroje služby SharePoint v sadě Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, debugging extensions
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5f878284c6e181956cbd3e708334301963aa25cf
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326092"
---
# <a name="debug-extensions-for-the-sharepoint-tools-in-visual-studio"></a>Ladění rozšíření pro nástroje služby SharePoint v sadě Visual Studio
  Můžete ladit rozšíření nástrojů služby SharePoint v experimentální instanci nebo normální instanci sady Visual Studio. Pokud potřebujete Poradce při potížích s chováním rozšíření, můžete také upravit hodnoty registru zobrazíte další informace o chybě a nakonfigurovat, jak Visual Studio provede příkazy služby SharePoint.

## <a name="debug-extensions-in-the-experimental-instance-of-visual-studio"></a>Ladění rozšíření v experimentální instanci sady Visual Studio
 K ochraně vývojového prostředí sady Visual Studio před náhodným poškozením netestovaným rozšířením, Visual Studio SDK poskytuje alternativní instanci sady Visual Studio, volá se *experimentální instanci*, který můžete použít k instalaci a testování rozšíření. Při vývoji nových rozšíření pomocí normální instanci sady Visual Studio, ale ladění a spouštění v experimentální instanci. Další informace najdete v tématu [experimentální instanci](../extensibility/the-experimental-instance.md).

 Pokud používáte k nasazení rozšíření projektu VSIX a projekt VSIX je projekt po spuštění ve vašem řešení, Visual Studio automaticky nainstaluje a spustí rozšíření v experimentální instanci při ladění řešení. Projekt po spuštění je projekt, který se spustí při ladění řešení, která obsahuje více projektů. Další informace o použití projektu VSIX k nasazení rozšíření najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Příklady, které ukazují, jak ladit různé typy rozšíření v experimentální instanci sady Visual Studio najdete v tématu následující kurzy:

-   [Návod: Rozšíření typu položky projektu SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)

-   [Návod: Vytvoření vlastní položky projektu akce pomocí šablony položky, část 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)

-   [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)

-   [Návod: Rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)

-   [Návod: Volání do modelu klientského objektu služby SharePoint v rozšíření Průzkumníka serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)

## <a name="debug-extensions-in-the-regular-instance-of-visual-studio"></a>Ladění rozšíření v normální instanci sady Visual Studio
 Pokud chcete k ladění projektu rozšíření v normální instanci sady Visual Studio, nejprve nainstalujte rozšíření v normální instanci. Potom připojte ladicí program k druhému procesu Visual Studio. Jakmile budete hotovi, můžete odebrat rozšíření tak, aby už načtenou ve vývojovém počítači.

#### <a name="to-install-the-extension"></a>Chcete-li nainstalovat rozšíření

1.  Zavřete všechny instance sady Visual Studio.

2.  V sestavení výstupní složky pro rozšíření projektu, otevřete *VSIX* soubor poklepáním nebo otevřením jeho místní nabídky a pak vyberete **otevřete**:

3.  V **instalační program Visual Studio rozšíření** dialogovém okně vyberte edice sady Visual Studio, do kterého chcete nainstalovat rozšíření a potom vyberte **nainstalovat** tlačítko.

     Visual Studio nainstaluje soubory rozšíření do %UserProfile%\AppData\Local\Microsoft\VisualStudio\11.0\Extensions\\*jméno autora*\\*název rozšíření* \\ *verze*. Poslední tři složky v této cestě se vytvářejí na základě `Author`, `Name`, a `Version` elementů v *extension.vsixmanifest* souboru rozšíření.

4.  Po instalaci rozšíření sady Visual Studio vyberte **Zavřít** tlačítko.

#### <a name="to-debug-the-extension"></a>Ladění rozšíření

1.  Spuštění sady Visual Studio s oprávněními správce a otevřete projekt rozšíření. Následující kroky odkazují na tuto instanci sady Visual Studio, jako *první instance*.

2.  Spusťte další instanci sady Visual Studio s oprávněními správce. Následující kroky odkazují na tuto instanci sady Visual Studio, jako *druhou instanci*.

3.  Přepnout na první instance sady Visual Studio.

4.  Na řádku nabídek zvolte **ladění**, **připojit k procesu**.

5.  V **dostupné procesy** vyberte *devenv.exe*. Tato položka odkazuje na druhou instanci sady Visual Studio; Toto je instance, kterou chcete ladit rozšíření vašeho projektu.

6.  Vyberte **Attach** tlačítko.

     Visual Studio spustí v režimu ladění rozšíření projektu.

7.  Přepnout na druhou instanci sady Visual Studio.

8.  Vytvoření nového projektu služby SharePoint, který načte rozšíření. Pokud ladíte rozšíření položek projektu definice seznamu, můžete například vytvořit **definice seznamu** projektu.

9. Provedení jakýchkoli kroků je nezbytné k testování kódu rozšíření.

10. Po dokončení ladění rozšíření zavřete druhou instanci sady Visual Studio.

#### <a name="to-remove-the-extension"></a>Chcete-li odebrat rozšíření

1.  V sadě Visual Studio na řádku nabídek zvolte **nástroje**, **rozšíření a aktualizace**.

     **Rozšíření a aktualizace** otevře se dialogové okno.

2.  V seznamu přípon, zvolte název daného rozšíření a potom **odinstalovat** tlačítko.

3.  V dialogovém okně, které se zobrazí, vyberte **Ano** tlačítko potvrďte, že chcete odinstalovat rozšíření.

4.  Vyberte **restartovat nyní** tlačítko k dokončení odinstalace.

## <a name="debug-sharepoint-commands"></a>Ladění SharePoint – příkazy
 Pokud chcete ladit příkaz SharePoint, který je součástí rozšíření nástrojů SharePoint, je nutné připojit ladicí program na *vssphost4.exe* procesu. Toto je 64bitová verze hostitele proces, který spouští příkazy služby SharePoint. Další informace o příkazech SharePoint a *vssphost4.exe*, najdete v části [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

#### <a name="to-attach-the-debugger-to-the-vssphost4exe-process"></a>Chcete-li proces vssphost4.exe připojit ladicí program

1.  Spusťte ladění rozšíření v experimentální instanci sady Visual Studio nebo normální instanci sady Visual Studio podle pokynů uvedených výše.

2.  V instanci sady Visual Studio, ve kterém běží ladicího programu, v řádku nabídek zvolte **ladění**, **připojit k procesu**.

3.  V **dostupné procesy** vyberte *vssphost.exe*.

    > [!NOTE]
    >  Pokud vssphost.exe v seznamu nezobrazí, musíte spustit *vssphost4.exe* procesů v instanci sady Visual Studio, ve kterém jsou spuštěna rozšíření. Obvykle to uděláte tak, že provedete akci, která způsobí, že chcete připojit k webu služby SharePoint na vývojovém počítači Visual Studio. Například Visual Studio spustí *vssphost4.exe* po rozbalení uzlu připojení k webu (uzel, který zobrazuje adresu URL webu) v části **připojení služby SharePoint** uzlu **Průzkumníka serveru**  okno, nebo když přidáte některé položky projektu služby SharePoint, jako například **instanci seznamu** nebo **příjemce událostí** položek do projektu služby SharePoint.

4.  Vyberte **Attach** tlačítko.

5.  V instanci sady Visual Studio, který je právě laděn proveďte kroky, které jsou nutné k provedení příkazu.

## <a name="modify-registry-values-to-help-debug-sharepoint-tools-extensions"></a>Upravit hodnot registru, které pomáhají ladit rozšíření nástrojů SharePoint
 Při ladění rozšíření nástrojů služby SharePoint v sadě Visual Studio, můžete změnit hodnoty v registru k vyřešení rozšíření. Hodnoty existovat pod **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\11.0\SharePointTools** klíč. Tyto hodnoty nejsou k dispozici ve výchozím nastavení.

 Pomoc při řešení potíží s jakékoli rozšíření nástrojů služby SharePoint, můžete vytvořit a nastavit hodnotu EnableDiagnostics. Následující tabulka popisuje tuto hodnotu.

|Hodnota|Popis|
|-----------|-----------------|
|EnableDiagnostics|REG_DWORD, která určuje, zda diagnostické zprávy se zobrazují v **výstup** okno.<br /><br /> Chcete-li zobrazit diagnostické zprávy, nastavte tuto hodnotu na 1. Zastavení, zobrazení zprávy, nastavte tuto hodnotu na 0 nebo tuto hodnotu odstraňte.<br /><br /> Zápis zpráv, které mají **výstup** rozšíření nástrojů okna ze služby SharePoint, použijte projektu služby SharePoint. Další informace najdete v tématu [použití služby projektu služby SharePoint](../sharepoint/using-the-sharepoint-project-service.md).|

 Pokud vaše rozšíření obsahuje příkaz SharePoint, můžete vytvořit a nastavte další hodnoty za účelem odstranění příkaz. Následující tabulka popisuje tyto hodnoty.

|Hodnota|Popis|
|-----------|-----------------|
|AttachDebuggerToHostProcess|REG_DWORD, která určuje, jestli se má zobrazit dialogové okno, která umožňuje připojit ladicí program na *vssphost4.exe* při jeho spuštění. To je užitečné, pokud příkaz, který chcete ladit spuštěn ve vssphost.exe ihned po jeho spuštění, a není k dispozici dostatek času na ručně připojit ladicí program před provedením příkazu. Chcete-li zobrazit dialogové okno, *vssphost4.exe* volání <xref:System.Diagnostics.Debugger.Break%2A> metoda po jeho spuštění.<br /><br /> Chcete-li toto chování, nastavte tuto hodnotu na 1. Chcete-li toto chování vypnout, nastavte tuto hodnotu na 0 nebo tuto hodnotu odstraňte.<br /><br /> Pokud tuto hodnotu nastavíte na 1, můžete také chtít zvýšit hodnotu HostProcessStartupTimeout, abyste měli dostatek času k připojit ladicí program, než se očekává v sadě Visual Studio *vssphost4.exe* signál, že je úspěšně spuštěn.|
|ChannelOperationTimeout|REG_DWORD, který určuje dobu v sekundách, který Visual Studio čeká k provedení příkazu SharePoint. Pokud příkaz nepracuje v čase, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> je vyvolána výjimka.<br /><br /> Výchozí hodnota je 120 sekundách.|
|HostProcessStartupTimeout|REG_DWORD, který určuje dobu v sekundách, sadou Visual Studio čeká na *vssphost4.exe* signál, že je úspěšně spuštěn. Pokud *vssphost4.exe* nevydá signál úspěšně spustit v průběhu času, <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException> je vyvolána výjimka.<br /><br /> Výchozí hodnota je 60 sekund.|
|MaxReceivedMessageSize|REG_DWORD, která určuje maximální povolenou velikost v bajtech zpráv WCF, které se předávají mezi sadou Visual Studio a *vssphost4.exe*.<br /><br /> Výchozí hodnota je 1 048 576 bajtů (1 MB).|
|MaxStringContentLength|REG_DWORD, která určuje maximální povolenou velikost v bajtech řetězců, které se předávají mezi sadou Visual Studio a *vssphost4.exe*.<br /><br /> Výchozí hodnota je 1 048 576 bajtů (1 MB).|

## <a name="see-also"></a>Viz také:

- [Rozšíření nástrojů SharePoint v sadě Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Nasazení rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
