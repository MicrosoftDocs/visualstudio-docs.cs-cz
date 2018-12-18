---
title: Refaktoring tříd a typů (návrhář tříd) | Dokumentace Microsoftu
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
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 215030b511ecbddbda23073df464035887f8ef95
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207958"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refaktoring tříd a typů (návrhář tříd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když refaktorujete kód, můžete bylo snazší porozumět, udržovat a efektivnější tak, že změníte její interní strukturu a způsobu jeho objektů navržena, není externí chování. Ke snížení práci, kterou musíte udělat a riziko zavlečení chyby při refaktorování kódu jazyka Visual C# .NET, Visual Basic .NET nebo C++ v projektu sady Visual Studio pomocí návrháře tříd a okně podrobností třídy.  
  
> [!NOTE]
>  Soubory projektu může být jen pro čtení, protože projekt je pod správou zdrojového kódu a není rezervován; jedná o Odkazovaný projekt; nebo jeho soubory označené jako jen pro čtení na disku. Při práci v projektu v jednom z těchto stavů, zobrazí se různé způsoby, jak uložit práci v závislosti na stavu projektu. To platí pro refaktoring kódu a také na kód, který změníte jiným způsobem, jako je například Přímá úprava. Další informace najdete v tématu [zobrazení jen pro čtení informací (návrhář tříd)](http://msdn.microsoft.com/en-us/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Obecné úlohy  
  
|Úloha|Podpůrný obsah|  
|----------|------------------------|  
|**Refaktoring tříd:** operace refaktoringu můžete použít k rozdělení třídy na částečné třídy nebo k implementaci abstraktní základní třídu.|-   [Postupy: rozdělení třídy na částečné třídy (návrhář tříd)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Práce s rozhraními:** v Návrháři tříd můžete implementovat rozhraní v diagramu tříd díky připojení k třídu, která poskytuje kód pro metody rozhraní.|-   [Postupy: implementace rozhraní (návrhář tříd)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refaktoring parametry, typy a členy typu:** pomocí návrháře tříd můžete přejmenovat typy, přepsat členy typu nebo je přesunout z jednoho typu na jiný. Můžete také vytvořit typy připouštějící hodnotu Null.|-   [Přejmenování typů a členů typu](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Přesunutí členy typu z jednoho typu na jiný](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Postupy: vytvoření typu s možnou hodnotou Null (návrhář tříd)](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
###  <a name="RenamingTypesAndMembers"></a> Přejmenování typů a členů typu  
 V Návrháři tříd můžete přejmenovat typ nebo člen typu v diagramu tříd nebo v okně Vlastnosti. V okně podrobností třídy můžete změnit název člena, ale není typu. Přejmenování typ nebo člen typu rozšíří pro všechna okna a kódem umístění, kde se nacházela původní název.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Chcete-li přejmenovat na název v Návrháři tříd  
  
1.  V diagramu tříd vyberte typ nebo člen a klikněte na název.  
  
     Název členu bude možné editovat.  
  
2.  Zadejte nový název pro tento typ nebo člen typu  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Chcete-li přejmenovat na název v okně podrobností třídy  
  
1.  Pokud chcete zobrazit v okně podrobností třídy, klikněte pravým tlačítkem na typ nebo člen typu a potom klikněte na **podrobností třídy**.  
  
     Zobrazí se okno podrobností třídy.  
  
2.  V **název** sloupce, změňte název členu typu  
  
3.  Chcete-li přesunout fokus z buňky, stiskněte **ENTER** klíče nebo klikněte na tlačítko mimo buňku.  
  
    > [!NOTE]
    >  V okně podrobností třídy můžete změnit název člena, ale není typu.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Chcete-li přejmenovat na název v okně Vlastnosti  
  
1.  V diagramu tříd nebo okně podrobností třídy klikněte pravým tlačítkem na tento typ nebo člen a pak klikněte na tlačítko **vlastnosti**.  
  
     V okně Vlastnosti se zobrazí vlastnosti pro tento typ nebo člen typu.  
  
2.  V **název** vlastnosti, změňte název typu nebo typ člena.  
  
     Nový název šíří pro všechna okna a umístění kódu v aktuálním projektu, kde se nacházela původní název.  
  
###  <a name="MovingTypeMembers"></a> Přesunutí členy typu z jednoho typu na jiný  
 Pomocí **návrhář tříd**, můžete přesunout člena typu z jednoho typu na jiný typ, pokud obě jsou viditelné v aktuálním diagramu tříd.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Přesunutí člena typu z jednoho typu na jiný  
  
1.  V typu, který je viditelný na návrhové ploše, klikněte pravým tlačítkem na člena, kterou chcete přesunout na jiný typ a potom klikněte na **Vyjmout**.  
  
2.  Klikněte pravým tlačítkem na typ cíle a potom klikněte na tlačítko **vložit**.  
  
     Vlastnost se odebere z typ zdroje a zobrazí se v cílovém typu.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Zobrazování typů a vztahů (Návrhář tříd)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Navrhování tříd a typů (Návrhář tříd)](../ide/designing-classes-and-types-class-designer.md)||



