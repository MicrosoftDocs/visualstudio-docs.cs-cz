---
title: Rozšiřování balení a nasazení služby SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967456"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Rozšiřování balení a nasazení služby SharePoint
  Můžete roztáhnout proces balení a nasazení pro projekty služby SharePoint.

## <a name="create-deployment-steps"></a>Vytvoření kroků nasazení
 Při nasazení projektu služby SharePoint [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] provede řada kroků nasazení. Visual Studio obsahuje integrované kroky nasazení pro mnoho úkolů, jako je odvolání a přidání řešení. Můžete ale také vytvořit vlastní kroky nasazení.

 Návod, který ukazuje, jak vytvořit krok nasazení, naleznete v tématu [Návod: Vytvoření vlastního kroku nasazení pro projekty služby SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Vytvoření konfigurací nasazení
 Konfigurace nasazení je sada kroků nasazení, které se spustí pro daný projekt, ale může mít vliv na všechny položky SharePointového projektu. Každá konfigurace nasazení zahrnuje jednu sadu kroků, která se spustí při nasazení projektu, a další sadu, která se spustí, když je projekt odvolán. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] obsahuje dvě předdefinované konfigurace nasazení, ale můžete také vytvořit vlastní. Při vytváření konfigurace nasazení můžete zahrnout integrované kroky nasazení a kroky nasazení, které vytvoříte.

 Návod, který ukazuje, jak vytvořit konfiguraci nasazení, naleznete v tématu [Návod: Vytvoření vlastního kroku nasazení pro projekty služby SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Spustit kód při nasazení nebo odvolání řešení služby SharePoint
 Můžete zpracovávat události a provádět další úkoly při nasazení nebo odvolání řešení služby SharePoint. Visual Studio vyvolává události, které můžete zpracovat v následujících scénářích:

- Před a po každém kroku nasazení se spustí pro položku SharePointového projektu. Další informace naleznete v tématu [How to: Run Code When a Deployment Steps](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Před a po nasazení nebo odvolání projektu služby SharePoint. Další informace naleznete v tématu [How to: Run Code When a server SharePoint je nasazen nebo odvolán](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Zpracování konfliktů nasazení
 Některé typy položek projektu služby SharePoint, včetně modulů, webových částí, instancí seznamů a typů obsahu, poskytují integrované řešení konfliktů nasazení. Když nasadíte řešení, které obsahuje jednu z těchto položek projektu, Visual Studio nejprve zkontroluje, zda soubor již existuje na webu služby SharePoint se stejným názvem, adresou URL nebo ID jako soubor v položce, kterou nasazujete. Pokud existuje konflikt, může Visual Studio automaticky vyřešit konflikt, nebo může zobrazit výzvu k určení, zda chcete, aby aplikace Visual Studio vyřešila konflikt nebo zrušilo nasazení. Další informace najdete v tématu [řešení potíží s balíčkem a nasazením služby SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Tuto funkci můžete roztáhnout tak, že poskytnete vlastní kód, který zkontroluje a vyřeší konflikty nasazení. Další informace naleznete v tématu [How to: Handle konflikty nasazení](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Spuštění operací příkazového řádku před nebo po nasazení projektu
 Pokud chcete spustit operaci příkazového řádku při nasazení řešení služby SharePoint, můžete nastavit <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> vlastnosti <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objektu a. Visual Studio provede tyto příkazy před a po nasazení projektu.

 V některých případech se může zobrazit konflikty nasazení. Existuje několik různých způsobů řešení konfliktů. Další informace najdete v tématu [řešení potíží s balíčkem a nasazením služby SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Přizpůsobení ověřovacích pravidel
 Před nasazením balíčku řešení (. wsp) můžete vytvořit vlastní funkce a pravidla pro ověření balíčku, abyste ověřili, že je funkce nebo balíček platná. Můžete například ohlásit informace, upozornění nebo chyby vývojářům, které jim pomohou při řešení problémů s ověřováním. Další informace najdete v tématu [Postupy: vytváření vlastních funkcí a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Viz také
- [Postupy: spuštění kódu při spuštění kroků nasazení](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Návod: Vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Postupy: Vytvoření vlastní funkce a pravidel ověřování balíčku pro řešení služby SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Rozšíří systém projektu služby SharePoint.](../sharepoint/extending-the-sharepoint-project-system.md)
