---
title: 'Návrhář postupu provádění - postupy: používání návrháře importů'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e26dafe6d8d7e455d1977f82f96f776185a5fdb3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845262"
---
# <a name="how-to-use-the-imports-designer"></a>Postupy: používání návrháře importů

Návrhář importů umožňuje zadejte obory názvů pro typy, které budete používat ve výrazech. Podobně jako **importuje** nebo **pomocí** klíčová slova v jazyce Visual Basic a C#, určení obory názvů v Návrhář importů umožňují jednoduše zadejte název typu ve výrazu spíše než plně Název typu kvalifikovaný verze.

Návrhář importů jsou reaguje na obě změny v uživatelském rozhraní a změny provedené při uložení pracovního postupu. Při uložení pracovního postupu, obory názvů může být automaticky přidán do návrháře importů. Patří mezi ně například:

- Obory názvů pro všechny typy použité v deklaracích proměnných a argumentů.

- Obory názvů pro všechny typy použité ve výrazech.

- Všechny ostatní obory názvů potřebné pro serializaci pracovního postupu (například oborů názvů používaných ve vlastní aktivity v pracovním postupu).

  Při uložení pracovní postup, můžete si všimnout, že některé obory názvů, který jste odstranili ručně jsou automaticky znovu přidat do návrháře importů z důvodu pravidla popsaná v předchozím seznamu.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Přidání nového oboru názvů na seznam importovaných oborů názvů

1.  Otevření aplikace služeb pracovního postupu WCF, konzolová aplikace pracovního postupu nebo projektu knihovny aktivity v sadě Visual Studio nebo aplikace pracovního postupu změněným hostováním.

2.  Klikněte na tlačítko **importy** v dolní části hlavního plátna. Zobrazí se Návrhář importů.

3.  Zadejte nebo vyberte z rozevíracího seznamu ovládacího prvku v horní části návrháře importů oboru názvů.

     Při psaní se zobrazí seznam platný obory názvů, které odpovídají zadané znaky.

4.  Stisknutím klávesy **Enter** do seznamu přidat obor názvů.

5.  Pokud chcete odebrat obor názvů v seznamu, vyberte obor názvů a potom stiskněte klávesu **odstranit** kláves na klávesnici. Všimněte si, že obor názvů můžete být odstraněno pouze tehdy, pokud obor názvů je neplatný z nějakého důvodu, například pokud sestavení, který obsahuje obor názvů je již odkazuje na projekt.