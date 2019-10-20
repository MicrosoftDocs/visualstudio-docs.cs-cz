---
title: 'Návrhář postupu provádění-postupy: použití návrháře Imports'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df019157b6a8bd6199b01a093efb422792804b3e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650267"
---
# <a name="how-to-use-the-imports-designer"></a>Postupy: použití návrháře Imports

Návrhář importů umožňuje zadat obory názvů pro typy, které budete používat ve svých výrazech. Podobně jako při **importu** nebo **použití** klíčových slov v Visual Basic C#a zadání obory názvů v Návrháři Imports vám umožní jednoduše zadat název typu ve výrazu místo plně kvalifikovaného názvu typu verze.

Návrhář importů reaguje na změny v uživatelském rozhraní a změny provedené při uložení pracovního postupu. Po uložení pracovního postupu lze obory názvů automaticky přidat do návrháře Imports. Patří mezi ně například:

- Obory názvů pro všechny typy používané v deklaracích proměnných a argumentů

- Obory názvů pro všechny typy používané ve výrazech

- Všechny ostatní obory názvů potřebné k serializaci pracovního postupu (například obory názvů používané vlastními aktivitami, které jsou v pracovním postupu vyhozeny).

  Když je pracovní postup uložen, můžete si všimnout, že některé obory názvů, které jste ručně odstranili, jsou automaticky znovu přidány do návrháře Imports z důvodu logiky popsané v předchozím seznamu.

## <a name="to-add-a-namespace-to-the-list-of-imported-namespaces"></a>Přidání oboru názvů do seznamu importovaných oborů názvů

1. Otevřete aplikaci služby pracovního postupu WCF, konzolovou aplikaci pracovního postupu nebo projektu knihovny aktivit v aplikaci Visual Studio nebo v přehostované aplikaci pracovního postupu.

2. V dolní části hlavního plátna klikněte na **Import** . Zobrazí se Návrhář importů.

3. V horní části návrháře importů zadejte nebo vyberte obor názvů z ovládacího prvku rozevírací seznam.

     Při psaní se zobrazí seznam platných oborů názvů, které odpovídají zadaným znakům.

4. Pokud chcete přidat obor názvů do seznamu, stiskněte klávesu **ENTER** .

5. Pokud chcete obor názvů odebrat ze seznamu, vyberte obor názvů a potom na klávesnici stiskněte klávesu **Delete** . Všimněte si, že obor názvů lze odstranit pouze v případě, že obor názvů je z jakéhokoli důvodu neplatný, například pokud sestavení, které obsahuje obor názvů, již není odkazováno v projektu.