---
title: Hostitelský proces (vshost.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a998246f514f13a575f6a7fef850f9f705f92553
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645532"
---
# <a name="hosting-process-vshostexe"></a>Proces hostování (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hostitelský proces je funkce v aplikaci Visual Studio, která vylepšuje výkon ladění, umožňuje ladění s částečným vztahem důvěryhodnosti a umožňuje vyhodnocování výrazů v době návrhu. Soubory procesu hostování obsahují VSHost v názvu souboru a jsou umístěny do výstupní složky vašeho projektu. Další informace naleznete v tématu [ladění a hostující proces](../debugger/debugging-and-the-hosting-process.md).

> [!NOTE]
> Soubory procesu hostování (.vshost.exe) jsou pro použití v aplikaci Visual Studio a neměly by být spouštěny přímo nebo nasazeny s vaší aplikací.

## <a name="improved-debugging-performance"></a>Vylepšený výkon ladění
 Hostitelský proces vytvoří doménu aplikace a přidruží ladicí program k aplikaci. Provádění těchto úloh může způsobit znatelné zpoždění mezi začátkem ladění a časem spuštění aplikace. Proces hostování pomáhá zvýšit výkon vytvořením aplikační domény a přidružením ladicího programu na pozadí a uložením aplikační domény a stavu ladicího programu mezi spuštění aplikace. Další informace o doménách aplikací naleznete v tématu [aplikační domény](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).

## <a name="partial-trust-debugging"></a>Ladění s částečným vztahem důvěryhodnosti
 Aplikace může být zadána jako aplikace s částečnou důvěryhodností na [stránce zabezpečení](../ide/reference/security-page-project-designer.md) **Návrháře projektu**. Ladění aplikace s částečnou důvěryhodností vyžaduje speciální inicializaci aplikační domény. Tato inicializace je zpracována hostitelským procesem.

## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu pro dobu návrhu
 Vyhodnocení výrazu v době návrhu umožňuje testovat kód z příkazového okna **bez** nutnosti spuštění aplikace. Hostitelský proces spustí tento kód během vyhodnocování výrazu pro dobu návrhu. Další informace naleznete v tématu [Immediate Window](../ide/reference/immediate-window.md).

## <a name="see-also"></a>Viz také
 [Ladění a hostující proces](../debugger/debugging-and-the-hosting-process.md) [Postup: zakázání hostitelského procesu](../ide/how-to-disable-the-hosting-process.md) [okamžité](../ide/reference/immediate-window.md) [aplikační domény](https://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)
