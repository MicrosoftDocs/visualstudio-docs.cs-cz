---
title: 'Postupy: vytvoření dědičnosti mezi typy (návrhář tříd) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5bcc052589f090eaad8aace8c491f74d3bbfefe9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257774"
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Postupy: vytvoření dědičnosti mezi typy (návrhář tříd) 
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vytvořit vztah dědičnosti mezi dvěma typy v diagramu tříd pomocí návrháře tříd, připojte pomocí jeho odvozeného typu základní typ nebo typy. Můžete mít vztah dědičnosti mezi dvěma třídami, mezi třídou a rozhraní nebo mezi dvě rozhraní.  
  
### <a name="to-create-an-inheritance-between-types"></a>Vytvoření dědičnosti mezi typy  
  
1.  Z projektu v Průzkumníku řešení otevřete soubor diagramu tříd (.cd).  
  
     Pokud nemáte k dispozici diagramu tříd, vytvořte ho. Zobrazit [postupy: Přidání diagramů tříd do projektů (návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  V **nástrojů**v části **návrhář tříd**, klikněte na tlačítko **dědičnosti**.  
  
3.  V diagramu tříd kreslení čáru dědičnosti mezi typy, které potřebujete, od:  
  
    -   Odvozené třídy základní třídy  
  
    -   Implementující třída s implementovaným rozhraním  
  
    -   Rozšíření rozhraní pro rozšířené rozhraní  
  
4.  Nebo pokud máte odvozeným typem od obecného typu, klikněte na čáru dědičnosti. V **vlastnosti** okno, nastavte **argumenty typu** vlastnost tak, aby odpovídaly typ, který chcete použít pro obecného typu.  
  
    > [!NOTE]
    >  Nadřazené abstraktní třídy obsahuje alespoň jeden abstraktní člen, jsou všechny abstraktní členy implementovány jako neabstraktní dědičné třídy.   
    >   
    >  I když můžete vizualizovat existující obecné typy, nelze vytvořit nové obecné typy. Také nelze změnit parametry typu pro existující obecné typy.  
  
## <a name="see-also"></a>Viz také  
 [Dědičnost](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)   
 [Základní informace o dědičnosti](http://msdn.microsoft.com/library/dfc8deba-f5b3-4d1d-a937-7cb826446fc5)   
 [Postupy: zobrazení dědičnosti mezi typy (návrhář tříd)](../ide/how-to-view-inheritance-between-types-class-designer.md)   
 [Třídy jazyka Visual C++ v Návrháři tříd](../ide/visual-cpp-classes-in-class-designer.md)



