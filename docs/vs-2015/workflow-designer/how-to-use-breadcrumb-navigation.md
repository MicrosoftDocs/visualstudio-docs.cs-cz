---
title: 'Postupy: použití navigace s popisem cesty | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 4a688056-37dc-406a-9071-be2141e192fe
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 19f9add69f8746962e6ed0ef9e4beea0f7ba37ec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259026"
---
# <a name="how-to-use-breadcrumb-navigation"></a>Postupy: použití navigace s popisem cesty
Existují tři hlavní způsoby, jak změnit sadu aktivit, které jsou zobrazeny v [!INCLUDE[wfd1](../includes/wfd1-md.md)]:  
  
1.  Dvakrát klikněte na Přejít k podřízené aktivity.  
  
2.  Klikněte na tlačítko na panelu navigace s popisem cesty a přejděte na nadřazenou aktivitou.  
  
3.  Rozbalit nebo sbalit aktivity na místě.  
  
### <a name="using-breadcrumb-navigation"></a>Pomocí navigace s popisem cesty  
  
1.  Dvakrát klikněte na aktivitu z [!INCLUDE[wfd2](../includes/wfd2-md.md)] změna kořenové aktivity na kliknutí na aktivity. Kliknutí na aktivitu poté plně rozbalen v kořenovém adresáři a jeho nadřazenými prvky jsou uvedeny na panelu navigace s popisem cesty. To se někdy nazývá procházení nebo z aktivity.  
  
2.  Pokud chcete přejít na nadřazena aktuální kořenové aktivity, klikněte na aktivitu v panelu s popisem cesty.  
  
### <a name="expanding-or-collapsing-an-activity-in-place"></a>Rozbalení a sbalení aktivitu na místě  
  
1.  Kliknutím na dvojité šipky pro aktivitu rozbalí nebo sbalí aktivity na místě.  
  
2.  Při změně stavu stavu rozbalení kliknutím na tlačítko Nový stav rozšíření je uložen v XAML.  
  
    > [!WARNING]
    >  Ne všechny aktivity lze rozšířit na místě. Existují dva možné případy, kdy aktivita nelze rozšířit na místě: buď nadřazené aktivity nepovoluje své podřízené objekty rozbalen v místě, (například aktivity ve vývojovém diagramu nelze rozšířit na místě), nebo Návrhář aktivity neumožňuje samotného Rozbalit na místě. I když žádné z návrháře aktivit, které jsou součástí [!INCLUDE[wfd2](../includes/wfd2-md.md)] mají druhé chování, některé vlastní aktivity může tímto způsobem chovat.  
  
### <a name="expanding-all-or-collapsing-all-activities"></a>Všechny rozbalení nebo sbalení všech aktivit  
  
1.  Použití **Rozbalit vše** a **Sbalit vše** tlačítka v uživatelském rozhraní pro rozbalení a sbalení všech aktivit v kořenovém adresáři aktuální navigace s popisem cesty. Všimněte si, že všechny rozbalit nebo sbalit všechny jsou globální stavy. To znamená, že když změníte kořenové aktivity pomocí navigace s popisem cesty, Rozbalit vše nebo sbalit všechny stavy opakuje dokud nekliknete na tlačítko **obnovení**.  
  
2.  Po použily všechny rozbalit nebo sbalit všechny stavy, můžete klepnout **obnovení** tlačítko, které se zobrazí chcete přejít zpátky k prohlížení stavu dříve použít u každé aktivity.  
  
    > [!WARNING]
    >  Pokud aktivitu, například <xref:System.Activities.Statements.Flowchart>, zvolil z rozbalit na místě, přidružený k funkci **Rozbalit vše** a **Sbalit vše** tlačítka je zakázán na **vývojový diagram**  návrháře. [!INCLUDE[crabout](../includes/crabout-md.md)] **vývojový diagram** návrháře, viz [vývojový diagram](../workflow-designer/flowchart-activity-designer.md) tématu.  
  
    > [!WARNING]
    >  Rozbalit vše má také zvláštní efekt v **přepínač** a **TryCatch** návrháři aktivit. Po kliknutí na **Rozbalit vše**, zobrazí se všechny switch case a všechny bloky konstrukce try/catch/finally. Kliknutím na **obnovení** nebo **Sbalit vše** vrací tyto návrháře do výchozího stavu, ve kterém můžete kliknout na jednotlivé případ nebo blok a zobrazit jeho obsah.