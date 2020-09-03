---
title: Výběr strategie implementace ladicího modulu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, implementation strategies
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6b03e69892da217d84d56b39b7df61784907d2b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183461"
---
# <a name="choosing-a-debug-engine-implementation-strategy"></a>Výběr strategie implementace ladicího stroje
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pomocí architektury za běhu určete strategii implementace ladicího modulu (DE). Ladicí stroj může být vytvořen v rámci procesu do programu, který má být laděn, v rámci procesu do aplikace Visual Studio Session Manager (SDM) nebo mimo proces do obou. Následující pokyny vám pomohou vybrat si z těchto tří strategií.  
  
## <a name="guidelines"></a>Pokyny  
 I když je možné, že je deladit do SDM a program, který se má ladit, většinou to není důvod. Volání napříč hranicemi procesů jsou poměrně pomalá.  
  
 Moduly ladění jsou již k dispozici pro prostředí Win32 Native runtime a pro prostředí společného jazykového modulu runtime. Pokud je nutné nahradit DE pro některá z těchto prostředí, je nutné vytvořit v rámci procesu SDM.  
  
 V opačném případě můžete zvolit mezi vytvořením procesu v rámci procesu SDM nebo v procesu do programu, který se má ladit. Je důležité zvážit, zda vyhodnocovací filtr výrazů DE potřebuje častý přístup k úložišti symbolů programu a zda lze úložiště symbolů načíst do paměti pro rychlý přístup. Zvažte také následující body:  
  
- Pokud mezi vyhodnocovacím filtrem výrazů a úložištěm symbolů neexistují žádná volání, nebo pokud lze úložiště symbolů načíst do paměťového prostoru SDM, vytvořte v procesu SDM proces DE in-Process. Je nutné, abyste při připojení k vašemu programu vrátili CLSID ladicího stroje do modelu SDM. Model SDM používá tento identifikátor CLSID k vytvoření instance v procesu DE.  
  
- Pokud DE musí volat program pro přístup k úložišti symbolů, vytvořte v programu příkaz DE in-Process. V tomto případě program vytvoří instanci DE.  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřitelnost programu Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
