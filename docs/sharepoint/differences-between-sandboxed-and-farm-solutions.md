---
title: Rozdíly mezi řešeními v izolovaném prostoru a farmách | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, sandboxed solutions
- sandboxed solutions [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, farm solutions
- farm solutions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 073e62b473ebfcec5f71ae1907e8f9e385333411
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967543"
---
# <a name="differences-between-sandboxed-and-farm-solutions"></a>Rozdíly mezi řešeními v izolovaném prostoru a farmách
  Když kompilujete řešení služby SharePoint, nasadí se na server SharePoint a ladicí program se připojí k ladění. Proces použitý k ladění řešení závisí na nastavení vlastnosti řešení v izolovaném prostoru: řešení v izolovaném prostoru nebo řešení farmy.

 Další informace najdete v tématu [požadavky na řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md).

## <a name="farm-solutions"></a>Řešení farmy
 Řešení farmy, která jsou hostována v pracovním procesu služby IIS (W3WP.exe), spouštějí kód, který může ovlivnit celou farmu. Při ladění projektu služby SharePoint, jehož vlastnost řešení v izolovaném prostoru je nastavena na "řešení farmy", dojde k recyklování fondu aplikací IIS systému před tím, než služba SharePoint vymění nebo nasadí funkci tak, aby uvolnila soubory uzamčené pracovním procesem služby IIS. Recykluje se pouze fond aplikací služby IIS obsluhující adresu URL webu projektu služby SharePoint.

## <a name="sandboxed-solutions"></a>Řešení v izolovaném prostoru
 Řešení v izolovaném prostoru, která jsou hostována v pracovním procesu řešení kódu uživatele služby SharePoint (SPUCWorkerProcess.exe), spouští kód, který může mít vliv pouze na kolekci webů řešení. Vzhledem k tomu, že řešení v izolovaném prostoru neběží v pracovním procesu služby IIS, není nutné restartovat fond aplikací služby IIS ani server IIS. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] připojí ladicí program k procesu SPUCWorkerProcess, který služba SPUserCodeV4 v SharePointu automaticky aktivuje a ovládá. Není nutné, aby se proces SPUCWorkerProcess recykloval, aby se načetla nejnovější verze řešení.

## <a name="either-type-of-solution"></a>Libovolný typ řešení
 V obou typech řešení [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také připojí ladicí program k prohlížeči, aby bylo možné povolit ladění skriptů na straně klienta. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] používá modul ladění skriptu pro tento účel. Pokud chcete povolit ladění skriptů, musíte po zobrazení výzvy změnit výchozí nastavení prohlížeče.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] připojí ladicí program pouze k procesům W3WP nebo SPUCWorkerProcess, na kterých běží aktuální lokalita. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] také připojí spravované moduly COM plus a modul pro ladění pracovního postupu.

## <a name="see-also"></a>Viz také
- [Ladění řešení služby SharePoint](../sharepoint/debugging-sharepoint-solutions.md)
- [Sestavování a ladění řešení služby SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [Otázky řešení v izolovaném prostoru](../sharepoint/sandboxed-solution-considerations.md)
