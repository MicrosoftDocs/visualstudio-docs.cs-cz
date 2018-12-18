---
title: Proces hostování (vshost.exe) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- vshost.exe
- hosting process
ms.assetid: c6b9e2be-f18d-4d75-ac52-56d55784734b
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d45da37dae805399f9af8591bcd017ed61a975c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49216693"
---
# <a name="hosting-process-vshostexe"></a>Proces hostování (vshost.exe)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hostitelský proces je funkce v sadě Visual Studio, který zlepšuje výkon ladění, umožňuje ladění v částečném vztahu důvěryhodnosti a umožňuje vyhodnocení výrazu pro dobu návrhu. Hostující proces soubory obsahují vshost v názvu souboru a jsou umístěny ve výstupní složce vašeho projektu. Další informace najdete v tématu [ladění a proces hostování](../debugger/debugging-and-the-hosting-process.md).  
  
> [!NOTE]
>  Hostování souborů procesu (. vshost.exe) jsou určeny pro použití v aplikaci Visual Studio a by neměl být přímo spustit nebo nasazen s aplikací.  
  
## <a name="improved-debugging-performance"></a>Vylepšení ladění výkonu  
 Hostitelský proces vytvoří aplikační doménu a ladicí program přidruží k aplikaci. Provádění těchto úkolů můžete zavést významnému zpoždění mezi ladění v době spuštění a čas aplikace zahájí spuštění. Hostitelský proces vám pomůže zvýšit výkon tím vytváření domény aplikace a přidružení ladicího programu na pozadí a uložíte domény aplikace a spustí ladicí program stavu mezi aplikace. Další informace o aplikačních doménách najdete v tématu [aplikačních doménách](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8).  
  
## <a name="partial-trust-debugging"></a>Ladění v částečném vztahu důvěryhodnosti  
 Aplikace se dá nastavit jako aplikace s částečnou důvěryhodností v [stránku zabezpečení](../ide/reference/security-page-project-designer.md) z **Návrháře projektu**. Ladění aplikace s částečnou důvěryhodností vyžaduje speciální inicializaci domény aplikace. Tato inicializace zařizuje služba hostitelský proces.  
  
## <a name="design-time-expression-evaluation"></a>Vyhodnocení výrazu v době návrhu  
 Vyhodnocení výrazu v době návrhu lze otestovat kód z **okamžité** okno bez nutnosti spuštění aplikace. Proces hostování tento kód provede během vyhodnocení výrazu pro dobu návrhu. Další informace najdete v tématu [podokna](../ide/reference/immediate-window.md).  
  
## <a name="see-also"></a>Viz také  
 [Ladění a proces hostování](../debugger/debugging-and-the-hosting-process.md)   
 [Postupy: zákaz procesu hostování](../ide/how-to-disable-the-hosting-process.md)   
 [Příkazové podokno](../ide/reference/immediate-window.md)   
 [Aplikační domény](http://msdn.microsoft.com/library/113a8bbf-6875-4a72-a49d-ca2d92e19cc8)



