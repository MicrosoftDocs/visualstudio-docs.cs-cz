---
title: Práce s diagramem definice DSL | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 1fc0dbc007dcb3e15891a4176fc5bdb96babbfa8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208582"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Práce s diagramem definice DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram [!INCLUDE[dsl](../includes/dsl-md.md)] definice je důležitý nástroj pro definice jazyka specifického pro doménu. Můžete přidat prvky k vaší doméně model a definování vztahů v diagramu a můžete upravit rozložení diagramu, aby byl lépe čitelný.  
  
## <a name="the-layout-of-the-diagram"></a>Rozložení diagramu  
 [!INCLUDE[dsl](../includes/dsl-md.md)] Diagramem definice má dva oddíly **třídám a vztahům** oddílu a **elementů diagramu** oddílu. **Třídám a vztahům** oddíl zobrazí doménovými třídami, vztahy domén a dědičnosti. **Elementů diagramu** oddílu zobrazí obrazec třídy, konektor, plavecké dráhy třídy a třídy generované diagramu návrháře.  
  
 Doménové třídy mohou objevit v několika umístěních v **třídám a vztahům** oddíly. Pokud je základní třídou pro jiné třídy domény a vztahy stromu, pokud je zdrojem vztahů obsažení nebo odkazu, zobrazí definici třídy domény stromové struktury dědičnosti. Třída zástupné domény se zobrazí jako cíle vztahů obsažení nebo odkazu. Ve výchozím nastavení, zástupný symbol prvky jsou zobrazeny s **vlastnosti domény** Sbalit oddíl. Dědičnost nebo vztahů obsažení nebo odkazu se nezobrazí.  
  
 Když přidáte doménovou třídou, se zobrazí v dolní části **třídám a vztahům** oddílu. Když přidáváte obsažení nebo odkazovat na relaci, jeho vykreslení v části a napravo od zdrojové doménové třídy.  
  
 Při přidávání doménových tříd a vztahů, může být obtížné vyhledat konkrétní doménovou třídu. Doménová třída můžete najít kliknutím pravým tlačítkem myši v **Průzkumník DSL** a pak levým na **najít v diagramu**.  
  
 Následující části popisují, jak změnit vzhled diagramu snadněji čitelné.  
  
## <a name="copying-elements"></a>Kopírování prvků  
 Můžete používat kopii, vyjmout a vložit na prvky v diagramem definice DSL.  
  
## <a name="zooming-in-or-out-on-the-diagram"></a>Přiblížení nebo oddálení v diagramu  
 Pomocí provést přiblížení nebo oddálení v diagramu **návrháře DSL** nástrojů k nastavení úrovně přiblížení.  
  
## <a name="hiding-map-lines"></a>Skrytí čáry mapy  
 Čáry mapy se řádky, které jsou vykreslovány vedle mezi doménovou třídu nebo vztah domény a tvar nebo konektor, ke které je namapován. Čáry mapy můžete skrýt kliknutím **zobrazit čáry mapy** tlačítko **návrháře DSL** nástrojů. Chcete-li zobrazit řádky, klikněte na tlačítko znovu.  
  
## <a name="changing-the-diagram-layout"></a>Změna rozložení diagramu  
 Můžete změnit rozložení **třídám a vztahům** oddílu následujícím způsobem.  
  
### <a name="expandcollapse"></a>Rozbalit/sbalit  
 Můžete zmenšit velikost elementu obrazce oddílu, který představuje doménovou třídu nebo obrazec s pravým tlačítkem myši a pak levým na **sbalit**. Tím **vlastnosti domény** obrazce oddílu. Chcete-li zobrazit **vlastnosti domény** oddílů znovu, klikněte pravým tlačítkem myši na obrazec a potom klikněte na **Rozbalit**.  
  
### <a name="move-updown"></a>Přesunout nahoru nebo dolů  
 Můžete přesunout domény tříd nebo diagramu prvek směrem nahoru nebo dolů v oddílu pravým tlačítkem myši prvek a potom klikněte na **nahoru** nebo **přesunout dolů**. Pokud přesunete prvek zástupného symbolu, který se zobrazí jako cíl vztahu obsažení nebo odkazu, relace se přesune s ním.  
  
### <a name="expandcollapse-relationships-tree"></a>Rozbalit nebo sbalit strom vztahů  
 Pokud doménová třída hraje roli zdroje v vztahů obsažení nebo odkazu pomocí jiné doménové třídy, lze skrýt vztahy pravým tlačítkem myši na definici třídy domény a poté klepnutím na **sbalit strom vztahů**. Zobrazit relace, klikněte pravým tlačítkem na element definice a potom klikněte na **rozbalte strom vztahů**.  
  
### <a name="expandcollapse-inheritance-tree"></a>Rozbalit nebo sbalit strom dědičnosti  
 Pokud doménová třída je základní třídou jiné třídy domény, můžete skrýt strom dědičnosti definice třídy domény pravým tlačítkem myši a potom klikněte na **sbalit strom dědičnosti**. Chcete-li zobrazit strom dědičnosti, klikněte pravým tlačítkem na element definice a potom klikněte na **rozbalte strom dědičnosti**.  
  
### <a name="bring-tree-here"></a>vložení stromu zde  
 Můžete konsolidovat v diagramu pravým tlačítkem myši na doménovou třídu zástupný text a potom klikněte na **přenést stromu zde**. Doménová třída zástupný symbol stane element definice a zobrazí dědičnost a vztahy stromů. Element původní definice stane prvek zástupného symbolu, pokud je cílem relace nebo podřízené v relaci dědičnosti; v opačném případě zmizí.  
  
### <a name="split-tree"></a>rozdělit strom  
 Můžete rozdělit stromové struktury dědičnosti nebo vztahy pravým tlačítkem myši na definici třídy domény, který zobrazí je a potom klikněte na **rozdělit strom**. Element definice stane zástupný prvek a definice doménová třída, společně s jeho dědičnost a vztahy stromů, se nyní zobrazí v dolní části oddílu.  
  
### <a name="show-as-class"></a>zobrazit jako třídu  
 Pokud doménovým vztahem obsahuje odvozené vztahů, nebo pokud má vztahů obsažení nebo odkazu pomocí jiné vztahy domén, můžete zobrazit vztah jako třídu kliknutím pravým tlačítkem vztah a pak levým na **zobrazit jako třídy** . Relace se zobrazí **vlastnosti domény** oddílů a zobrazí stromů dědičnost a vztahy.  
  
## <a name="see-also"></a>Viz také  
 [Glosář nástrojů jazyka specifického pro doménu](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



