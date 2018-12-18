---
title: Volání do Sharepointu objektových modelů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 3afb988b226ccf62fae92ab02d8380d20b19605b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853426"
---
# <a name="call-into-the-sharepoint-object-models"></a>Volání do objektových modelů služby SharePoint
  Při vytváření rozšíření pro nástroje služby SharePoint v sadě Visual Studio, bude pravděpodobně k volání rozhraní API služby SharePoint k provádění určitých úloh. Pokud vytvoříte vlastního kroku nasazení pro projekty služby SharePoint, budete muset volat rozhraní API služby SharePoint k provedení některých úkolů k nasazení řešení.  
  
 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] poskytují dvě různé objektové modely, které vám v rozšíření nástrojů služby SharePoint: objektový model serveru a objektového modelu klienta. Každý model objektu má své výhody a nevýhody v rámci rozšíření nástrojů služby SharePoint.  
  
 Přehled objektových modelů služby SharePoint, naleznete v tématu [Přehled programovacího modelu SharePoint rozšíření nástrojů](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).  
  
## <a name="use-the-client-object-model-in-extension-projects"></a>Použití objektového modelu klienta v rozšíření projektů
 Při vývoji rozšíření pro nástroje služby SharePoint, můžete použít objektového modelu klienta ve vašem projektu, jako je sada spravovaných rozhraní API. Odkazy na sestavení v objektovém modelu klienta můžete přidat do projektu a můžete volat rozhraní API v objektovém modelu klienta přímo z uživatelského kódu.  
  
 Objektového modelu klienta má dvě nevýhod ale v rámci rozšíření nástrojů SharePoint:  
  
- Objektový model klienta obsahuje pouze podmnožinu objektový model serveru. Pokud budete muset použít funkce služby SharePoint, který není vystavený v objektovém modelu klienta, musíte použít objektový model serveru.  
  
- I když ve většině případů by měl fungovat v rozšíření nástrojů služby SharePoint pomocí objektového modelu klienta, může dojít k některé scénáře, ve kterém volání do objektového modelu klienta nefungují podle očekávání. Objektového modelu klienta je určen pro použití v klientské aplikace provést volání do webů služby SharePoint na vzdáleném serveru nebo farmy. Nástroje služby SharePoint v sadě Visual Studio fungovat jenom s místní instalace služby SharePoint ve vývojovém počítači. Proto při použití objektového modelu klienta v rozšíření nástrojů SharePoint volat do webu služby SharePoint v místním počítači, který je jak nebyl navržen objektového modelu klienta, který se má použít.  
  
  Návod, který demonstruje použití objektového modelu klienta v rozšíření nástrojů SharePoint v sadě Visual Studio, naleznete v tématu [návod: volání do objektového modelu klienta SharePoint v rozšíření Průzkumníka serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).  
  
## <a name="use-the-server-object-model-in-extension-projects"></a>Objektový model serveru používané k rozšíření projektů
 Objektový model serveru je nadstavbou jazyka objektového modelu klienta. Když použijete objektový model serveru, můžete použít všechny funkce, která [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] zveřejnit prostřednictvím kódu programu.  

 Rozšíření nástrojů služby SharePoint můžete použít rozhraní API v objektovém modelu serveru, ale nelze přímo volat rozhraní API. Objektový model serveru lze volat pouze z 64bitový proces, který cílí rozhraní .NET Framework 3.5. Ale vyžadují rozšíření nástrojů SharePoint [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a provozují v 32bitový proces sady Visual Studio. To zabrání rozšíření nástrojů SharePoint přímo odkazuje na sestavení v objektovém modelu serveru SharePoint.  
  
 Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je třeba vytvořit vlastní *příkaz serveru SharePoint* pro volání rozhraní API. Definování příkazu Sharepointu v sekundárním sestavení, které můžete volat přímo do objektového modelu serveru. V projektu rozšíření, můžete volat příkaz serveru SharePoint nepřímo pomocí metody ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu.  
  
 Další informace o vytváření a použití příkazů služby SharePoint, naleznete v tématu [postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md) a [postup: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Informace o tom, jak nasadit příkazů služby SharePoint, naleznete v tématu [nasadit rozšíření pro nástroje služby SharePoint v sadě Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
 Návody, které ukazují, jak vytvořit a používat příkazy služby SharePoint, naleznete v tématu [návod: vytvoření vlastního kroku nasazení pro projekty SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) a [návod: rozšíření Průzkumníka serveru pro zobrazení částí webu ](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).  
  
### <a name="understand-how-sharepoint-commands-are-executed"></a>Vysvětlení, jak jsou spouštěny příkazy služby SharePoint
 Sestavení, které definují příkazů služby SharePoint jsou načteny v 64bitový hostitelský proces s názvem *vssphost4.exe*. Po volání příkazu SharePoint v rozšíření nástrojů SharePoint ve spuštění příkazu *vssphost4.exe* místo 32bitový proces sady Visual Studio (*devenv.exe*). Můžete ovládat některé aspekty jak jsou spouštěny příkazy služby SharePoint pomocí nastavení hodnoty v registru. Další informace najdete v tématu [rozšíření pro nástroje služby SharePoint v sadě Visual Studio pro ladění](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).  
  
## <a name="see-also"></a>Viz také:
 [Postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)   
 [Postupy: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)   
 [Přehled programovacího modelu SharePoint rozšíření nástrojů](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)  
  
