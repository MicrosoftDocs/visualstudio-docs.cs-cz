---
title: Rozdíly mezi řešeními v izolovaném prostoru a ve farmách | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 282fe23a9a586d79b745efec99bc014e88777fd6
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326329"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Rozdíly mezi řešeními v izolovaném prostoru a ve farmách
  Při kompilaci řešení služby SharePoint se nasadí do serveru SharePoint a ladicí program připojí k ladění. Proces používaný k ladění řešení závisí na nastavení vlastnosti řešení v izolovaném prostoru: řešení v izolovaném prostoru nebo řešení farmy.  
  
 Další informace najdete v tématu [aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).  
  
## <a name="farm-solutions"></a>Řešení ve farmách
 Řešení ve farmách, které jsou hostované v pracovním procesu služby IIS (W3WP.exe), spusťte kód, který může mít vliv na celou farmu. Při ladění projektu služby SharePoint, jehož vlastnost řešení v izolovaném prostoru je nastavena na "řešení farmy" recykluje fond aplikací služby IIS systému před SharePoint odvolá nebo nasadí funkci tak, aby se uvolnit všechny soubory uzamčený pracovní proces služby IIS. Recyklován pouze fond aplikací služby IIS obsluhující adresa URL webu projektu služby SharePoint.  
  
## <a name="sandboxed-solutions"></a>Řešení v izolovaném prostoru
 Řešení v izolovaném prostoru, které jsou hostované v pracovním procesu služby SharePoint uživatele kód řešení (SPUCWorkerProcess.exe), spustit kód, který může ovlivnit pouze kolekce webů řešení. Protože řešení v izolovaném prostoru se nespustí v pracovním procesu služby IIS, musíte restartovat fondu aplikací služby IIS ani server služby IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] připojí ladicí program k ovládacím prvkům a SPUCWorkerProcess proces, který automaticky aktivuje SPUserCodeV4 služby ve službě SharePoint. Není nutné pro proces SPUCWorkerProcess recyklace načíst nejnovější verzi řešení.  
  
## <a name="either-type-of-solution"></a>Buď zadejte řešení
 S typem buď řešení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také připojí ladicí program do prohlížeče, které chcete povolit ladění skriptů na straně klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá skript ladění modul pro tento účel. Pokud chcete povolit ladění skriptů, musíte změnit výchozí nastavení prohlížeče při zobrazení výzvy.  
  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] připojí ladicí program pouze pro W3WP nebo SPUCWorkerProcess procesy, které jsou spuštěné aktuální lokalitě. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] připojí také spravované COM Plus a pracovní postup ladění moduly.  
  
## <a name="see-also"></a>Viz také:
 [Ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md)   
 [Vytváření a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)   
 [Aspekty řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md)  
  
