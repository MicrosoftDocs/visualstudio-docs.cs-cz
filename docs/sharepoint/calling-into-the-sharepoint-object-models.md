---
title: Volání do objektových modelů služby SharePoint | Microsoft Docs
description: Pochopte, jak volat do dvou různých objektových modelů, které lze použít v rozšířeních nástrojů služby SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40cd7132888d8b19d8e2a2818ec9a299b465e786
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850049"
---
# <a name="call-into-the-sharepoint-object-models"></a>Volání do objektových modelů služby SharePoint
  Při vytváření rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio může být nutné volat rozhraní API služby SharePoint k provedení určitých úkolů. Například pokud vytvoříte vlastní krok nasazení pro projekty služby SharePoint, může být nutné volat rozhraní API služby SharePoint, aby bylo možné provést některé úlohy pro nasazení řešení.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] poskytují dva různé objektové modely, které lze použít v rozšíření nástrojů služby SharePoint: objektový model serveru a klientský objektový model. Každý objektový model má v kontextu rozšíření nástrojů služby SharePoint výhody a nevýhody.

 Přehled modelů objektů služby SharePoint naleznete v tématu [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Použití objektového modelu klienta v projektech rozšíření
 Při vývoji rozšíření pro nástroje služby SharePoint můžete použít objektový model klienta v projektu stejně jako jakákoli jiná sada spravovaných rozhraní API. Do projektu můžete přidat odkazy na sestavení v objektovém modelu klienta a můžete volat rozhraní API v modelu objektu klienta přímo z vašeho kódu.

 Model objektu klienta má však dvě nevýhody v kontextu rozšíření nástrojů služby SharePoint:

- Objektový model klienta poskytuje pouze podmnožinu objektového modelu serveru. Pokud je nutné použít funkce služby SharePoint, které nejsou vystaveny v modelu objektu klienta, je nutné použít objektový model serveru.

- I když použití objektového modelu klienta v rozšířeních nástrojů služby SharePoint by mělo fungovat ve většině případů, může dojít k některým scénářům, kdy volání klientského objektového modelu nefungují podle očekávání. Objektový model klienta je navržený tak, aby se mohl používat v klientských aplikacích pro volání na weby služby SharePoint na vzdáleném serveru nebo farmě. Nástroje služby SharePoint v aplikaci Visual Studio fungují pouze s místní instalací služby SharePoint ve vývojovém počítači. Proto při použití objektového modelu klienta v rozšíření nástrojů služby SharePoint zavoláte na web služby SharePoint v místním počítači, který nezpůsobí použití modelu klientského objektu.

  Návod, který ukazuje použití modelu objektu klienta v rozšíření nástrojů služby SharePoint v aplikaci Visual Studio, naleznete v tématu [Návod: volání do modelu objektu klienta služby SharePoint v rozšíření Průzkumník serveru](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Použití objektového modelu serveru v projektech rozšíření
 Objektový model serveru je nadmnožinou objektového modelu klienta. Při použití objektového modelu serveru můžete použít všechny funkce, které [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] a [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] vystavení programově.

 Rozšíření nástrojů služby SharePoint mohou používat rozhraní API v objektovém modelu serveru, ale nemohou přímo volat rozhraní API. Objektový model serveru lze volat pouze z 64 procesu, který cílí na .NET Framework 3,5. Rozšíření nástrojů služby SharePoint však vyžadují [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] a spouštěna v procesu 32 sady Visual Studio. To brání rozšíření nástrojů služby SharePoint v odkazování na sestavení v objektovém modelu serveru SharePoint přímo.

 Pokud chcete použít objektový model serveru v rozšíření nástrojů služby SharePoint, je nutné vytvořit vlastní *příkaz SharePointu* pro volání rozhraní API. Příkaz SharePoint definujete v sekundárním sestavení, které může přímo zavolat do modelu objektu serveru. V projektu rozšíření zavoláte příkaz SharePoint nepřímo pomocí metody ExecuteCommand <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> objektu.

 Další informace o vytváření a používání příkazů služby SharePoint naleznete v tématu [How to: Create a SharePoint Command](../sharepoint/how-to-create-a-sharepoint-command.md) and [to: Execute a Command SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md). Informace o tom, jak nasadit příkazy služby SharePoint, naleznete v tématu [nasazení rozšíření pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 Návody, které ukazují, jak vytvořit a používat příkazy služby SharePoint, naleznete v tématu [Návod: Vytvoření vlastního kroku nasazení pro projekty služby SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) a [Návod: roztažení Průzkumník serveru pro zobrazení webových částí](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>Pochopení způsobu spuštění příkazů služby SharePoint
 Sestavení, která definují příkazy služby SharePoint, jsou načtena v 64 hostitelském procesu s názvem *vssphost4.exe*. Po volání příkazu SharePoint v rozšíření nástrojů služby SharePoint je příkaz proveden pomocí *vssphost4.exe* namísto procesu 32 sady Visual Studio (*devenv.exe*). Nastavením hodnot v registru můžete řídit některé aspekty, jak se spouštějí příkazy služby SharePoint. Další informace naleznete v tématu [rozšíření ladění pro nástroje služby SharePoint v aplikaci Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Viz také
- [Postupy: vytvoření příkazu SharePoint](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Postupy: provedení příkazu SharePoint](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [Přehled programovacího modelu rozšíření nástrojů služby SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
