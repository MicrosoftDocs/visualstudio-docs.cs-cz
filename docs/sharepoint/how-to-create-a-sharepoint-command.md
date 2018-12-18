---
title: 'Postupy: vytvoření příkazu SharePoint | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint commands [SharePoint development in Visual Studio], creating
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 89384a1bf095b27f97be46ae303148ab5f8c7d1f
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37117134"
---
# <a name="how-to-create-a-sharepoint-command"></a>Postupy: vytvoření příkazu SharePoint
  Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je třeba vytvořit vlastní *příkazu SharePoint* pro volání rozhraní API. Příkaz SharePoint definujete v sestavení, které můžete volat přímo do objektový model serveru.  
  
 Další informace o účelu SharePoint – příkazy najdete v tématu [volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
### <a name="to-create-a-sharepoint-command"></a>Vytvoření příkazu SharePoint  
  
1.  Vytvoření projektu knihovny tříd, který má následující konfiguraci:  
  
    -   Cíle rozhraní .NET Framework 3.5. Další informace o výběru cílové rozhraní najdete v tématu [postupy: cílení na verzi rozhraní .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).  
  
    -   Cílem AnyCPU nebo x64 platformy. Ve výchozím nastavení je cílová platforma u projektů knihovny tříd AnyCPU. Další informace o výběru cílové platformy najdete v tématu [postupy: Konfigurace projektů pro cílové platformy](../ide/how-to-configure-projects-to-target-platforms.md).  
  
    > [!NOTE]  
    >  Příkaz SharePoint nelze implementovat ve stejném projektu, který definuje rozšíření nástrojů SharePoint, protože cílové rozhraní .NET Framework 3.5 a SharePoint cíl rozšíření nástrojů SharePoint – příkazy [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Je nutné definovat všechny příkazy služby SharePoint, které používají rozšíření v projektu samostatné. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
2.  Přidejte odkazy na následující sestavení:  
  
    -   Microsoft.VisualStudio.SharePoint.Commands  
  
    -   Microsoft.SharePoint  
  
3.  Ve třídě v projektu vytvoření metody, která definuje příkazu SharePoint. Metoda musí splňovat následující pokyny:  
  
    -   Může mít jeden nebo dva parametry.  
  
         Musí být první parametr <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> objektu. Tento objekt obsahuje Microsoft.SharePoint.SPSite nebo Microsoft.SharePoint.SPWeb, ve kterém se spustí příkaz. Poskytuje také <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandLogger> objekt, který slouží k zápisu zprávy a pokuste se **výstup** okno nebo **seznam chyb** oken v sadě Visual Studio.  
  
         Druhý parametr může být typ vlastního výběru, ale tento parametr je volitelný. Tento parametr můžete přidat do příkazu SharePoint, pokud potřebujete předat data z rozšíření nástrojů služby SharePoint do příkazu.  
  
    -   Může mít návratovou hodnotu, ale tato položka je nepovinná.  
  
    -   Druhý parametr a vraťte se hodnota musí být typ, který lze serializovat ve Windows Communication Foundation (WCF). Další informace najdete v tématu [typy nepodporuje serializátor kontraktu dat](/dotnet/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer) a [používání třídy XmlSerializer](/dotnet/framework/wcf/feature-details/using-the-xmlserializer-class).  
  
    -   Metoda může mít žádné viditelnost (**veřejné**, **interní**, nebo **privátní**), a může být statické nebo nestatické.  
  
4.  Použít <xref:Microsoft.VisualStudio.SharePoint.Commands.SharePointCommandAttribute> metodě. Tento atribut určuje jedinečný identifikátor pro příkaz; Tento identifikátor nemusí odpovídat názvu metody.  
  
     Při volání příkazu z rozšíření nástrojů služby SharePoint, musíte zadat stejný jedinečný identifikátor. Další informace najdete v tématu [postup: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje příkazu SharePoint, který má identifikátor `Contoso.Commands.UpgradeSolution`. Tento příkaz používá rozhraní API v objektovém modelu serveru k upgradu nasazené řešení.  
  
 [!code-csharp[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/CSharp/UpgradeDeploymentStep/SharePointCommands/Commands.cs#5)]
 [!code-vb[SPExtensibility.ProjectExtension.UpgradeDeploymentStep#5](../sharepoint/codesnippet/VisualBasic/upgradedeploymentstep/sharepointcommands/commands.vb#5)]  
  
 Kromě implicitní první <xref:Microsoft.VisualStudio.SharePoint.Commands.ISharePointCommandContext> parametr, tento příkaz má také parametr vlastní řetězec, který obsahuje úplnou cestu souboru WSP, která se upgraduje na stránku služby SharePoint. Tento kód v rámci většího příkladu najdete v sekci [návod: vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje odkazy na následující:  
  
-   Microsoft.VisualStudio.SharePoint.Commands  
  
-   Microsoft.SharePoint  
  
## <a name="deploying-the-command"></a>Příkaz nasazení  
 K nasazení příkaz, zahrnují sestavení příkazu ve stejné [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] rozšíření (*vsix*) balíček s sestavení rozšíření, která pomocí příkazu. Musíte taky přidat položku pro příkaz sestavení v souboru extension.vsixmanifest. Další informace najdete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Volání do objektových modelů služby SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [Postup: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Návod: Rozšíření Průzkumníka serveru pro zobrazení webové části](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
