---
title: Zajistit jeho důvěryhodnost do dokumentů
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- security [Office development in Visual Studio], trust
- inclusion lists [Office development in Visual Studio], about inclusion lists
- trust [Office development in Visual Studio], 2007 Office system
- granting trust [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5dfa0ad9b27b94c472feabc0e202bd9eee58f08d
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50670907"
---
# <a name="grant-trust-to-documents"></a>Zajistit jeho důvěryhodnost do dokumentů
  Úrovni dokumentu projekt má stejné požadavky na zabezpečení jako projekty na úrovni aplikace: podepisování manifestů s certifikátem nebo kliknutím na výzvu vztahu důvěryhodnosti. Kromě toho dokumentem nebo sešitem, musí být umístěn v adresáři, který je určený jako důvěryhodného umístění.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="trusted-locations"></a>Důvěryhodná umístění  
 Aplikace v [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a Office 2010 centra vztahu důvěryhodnosti, kde uživatelé můžou konfigurovat nastavení zabezpečení a ochrana osobních údajů, jako je například důvěryhodných umístění. Pro řešení Office místním počítači se považuje za důvěryhodného umístění. Kvůli vyššímu riziku, existují však určité adresáře, která se nesmí nikdy důvěryhodné, jako je například dočasných složek pro systém, pro každého uživatele a pro Internet Explorer.  
  
 Další informace o Centru zabezpečení najdete v tématu [zabezpečení a zásady a nastavení v aplikaci Office 2010](http://go.microsoft.com/fwlink/?LinkId=89202). Další informace o tom, jak vytvořit, spravovat, odebrat a konfigurovat důvěryhodné složky, najdete v části [nakonfigurovat důvěryhodné umístění a nastavení důvěryhodných vydavatelů v systému Office 2007](http://go.microsoft.com/fwlink/?LinkId=89203) a [vytvořit, odebrat nebo změnit důvěryhodné umístění souborů](https://support.office.com/article/Create-remove-or-change-a-trusted-location-for-your-files-f5151879-25ea-4998-80a5-4208b3540a62).  
  
## <a name="security-considerations-for-office-solutions"></a>Informace o zabezpečení pro řešení pro systém Office  
 Existuje několik otázky zabezpečení při zvažování složky, které chcete přidat do seznamu důvěryhodných umístění:  
  
-   Místní složky jsou považovány za další zabezpečení a jsou implicitně důvěryhodné. Vzdálených umístěních, jako jsou sdílené složky musí být určena jako důvěryhodných umístění.  
  
-   Když přidáte do seznamu důvěryhodných umístění adresáře, tato akce uděluje úplný vztah důvěryhodnosti, nejen pro řešení pro Office, ale také pro kód VBA a ActiveX. Z tohoto důvodu, kořenový adresář a *dokumenty* složky by neměl být určen jako důvěryhodné.  
  
-   I když samotný dokument je důvěryhodný pro používání důvěryhodných umístění, další oprávnění jsou nutná k přizpůsobení důvěřovat. Můžete udělit úplný vztah důvěryhodnosti k přizpůsobení pomocí podepisování manifestů s certifikátem, klepnutím na výzvu vztahu důvěryhodnosti nebo instalací řešení Office tak, aby *Program Files* adresáře.  
  
-   Můžete ukládat dokumentem nebo sešitem, řešení úrovni dokumentu ve stejném adresáři jako sestavení nebo v jiném adresáři. Například dokument může nacházet na serveru SharePoint server a sestavení nebyly nalezeny ve sdílené síti. Další informace najdete v tématu [postupy: publikování řešení Office úrovni dokumentu na SharePoint serveru s použitím technologie ClickOnce](https://msdn.microsoft.com/2408e809-fb78-42a1-9152-00afa1522e58).  
  
## <a name="see-also"></a>Viz také:  
 [Zajistit jeho důvěryhodnost do řešení pro systém Office](../vsto/granting-trust-to-office-solutions.md)   
 [Řešení potíží se zabezpečením řešení pro systém Office](../vsto/troubleshooting-office-solution-security.md)   
 [Zabezpečení řešení pro systém Office](../vsto/securing-office-solutions.md)  
  
  