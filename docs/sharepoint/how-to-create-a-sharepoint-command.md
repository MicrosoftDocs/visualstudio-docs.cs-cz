---
title: 'Postupy: vytvoření příkazu SharePointu | Microsoft Docs'
description: Naučte se vytvořit vlastní příkaz SharePointu, který bude volat rozhraní API modelu objektu serveru v rozšíření nástrojů služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7cc3d29d4991b6cfb712e4754f066edbb66f0b71
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216680"
---
# <a name="how-to-create-a-sharepoint-command"></a>Postupy: vytvoření příkazu SharePoint
  Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je nutné vytvořit vlastní *příkaz SharePointu* pro volání rozhraní API. Příkaz SharePoint definujete v sestavení, které lze přímo volat do objektového modelu serveru.

 Další informace o účelu příkazů služby SharePoint naleznete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).

### <a name="to-create-a-sharepoint-command"></a>Vytvoření příkazu SharePoint

1. Vytvořte projekt knihovny tříd, který má následující konfiguraci:

    - Cílí na .NET Framework 3,5. Další informace o výběru cílové architektury naleznete v tématu [How to: Target a version of .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

    - Cílí na platformu AnyCPU nebo x64. Ve výchozím nastavení je cílová platforma pro projekty knihovny tříd AnyCPU. Další informace o výběru cílové platformy najdete v tématu [Postupy: konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).

    > [!NOTE]
    > Příkaz SharePoint nelze implementovat ve stejném projektu, který definuje rozšíření nástrojů služby SharePoint, protože příkazy služby SharePoint cílí na .NET Framework 3,5 a rozšíření nástrojů služby SharePoint cílí na [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Musíte definovat všechny příkazy služby SharePoint, které vaše rozšíření používá v samostatném projektu. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

2. Přidejte odkazy na následující sestavení:

    - Microsoft. VisualStudio. SharePoint. Commands

    - Microsoft. SharePoint

3. Ve třídě projektu vytvořte metodu definující příkaz služby SharePoint. Metoda musí splňovat následující pokyny:

    - Může mít jeden nebo dva parametry.

         Prvním parametrem musí být <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objekt. Tento objekt poskytuje Microsoft. SharePoint. SPSite nebo Microsoft. SharePoint. SPWeb, ve kterém se příkaz spustí. Poskytuje také <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objekt, který lze použít k zápisu zpráv do okna **výstupu** nebo okna **Seznam chyb** v aplikaci Visual Studio.

         Druhý parametr může být zvoleným typem, ale tento parametr je nepovinný. Tento parametr můžete přidat do příkazu služby SharePoint, pokud potřebujete předat data z rozšíření nástrojů služby SharePoint do příkazu.

    - Může mít návratovou hodnotu, ale to je volitelné.

    - Druhý parametr a návratová hodnota musí být typ, který může být serializován pomocí Windows Communication Foundation (WCF). Další informace najdete v tématu [typy podporované serializátorem kontraktu dat](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) a [pomocí třídy XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).

    - Metoda může mít libovolnou viditelnost (**Public**, **internal** nebo **Private**) a může být statická nebo nestatická.

4. Použijte <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> pro metodu. Tento atribut určuje jedinečný identifikátor příkazu. Tento identifikátor nemusí odpovídat názvu metody.

     Při volání příkazu z rozšíření nástrojů služby SharePoint je nutné zadat stejný jedinečný identifikátor. Další informace naleznete v tématu [How to: Execute a SharePoint Command](../sharepoint/how-to-execute-a-sharepoint-command.md).

## <a name="example"></a>Příklad
 Následující příklad kódu ukazuje příkaz SharePointu, který má identifikátor `Contoso.Commands.UpgradeSolution` . Tento příkaz používá rozhraní API v objektovém modelu serveru k upgradu na nasazené řešení.

 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs" id="Snippet5":::
 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb" id="Snippet5":::

 Kromě implicitního prvního <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametru má tento příkaz také parametr vlastního řetězce, který obsahuje úplnou cestu k souboru. wsp, který je upgradován na web služby SharePoint. Chcete-li zobrazit tento kód v kontextu většího příkladu, přečtěte si [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="compiling-the-code"></a>Zkompilování kódu
 Tento příklad vyžaduje odkazy na následující sestavení:

- Microsoft. VisualStudio. SharePoint. Commands

- Microsoft. SharePoint

## <a name="deploying-the-command"></a>Nasazení příkazu
 Chcete-li nasadit příkaz, zahrňte sestavení příkazu do stejného [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] balíčku rozšíření (*VSIX*) se sestavením rozšíření, které používá příkaz. Také je nutné přidat položku pro sestavení příkazu v souboru extension. vsixmanifest. Další informace naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)
- [Postupy: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
