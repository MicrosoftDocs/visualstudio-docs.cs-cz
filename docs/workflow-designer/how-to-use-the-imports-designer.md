---
title: 'Návrhář postupu provádění-postupy: použití návrháře Imports'
description: Přečtěte si, jak návrhář importů umožňuje zadat obory názvů pro typy, které budete používat ve svých výrazech.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.View.ImportDesigner.UI
ms.assetid: 61328ab6-9b66-4e12-8630-22e30ee8c9d1
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fd736c01843d746ee43a82e6bb6f5239da1c660e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894046"
---
# <a name="how-to-use-the-imports-designer"></a>Postupy: Používání návrháře importů

Návrhář importů umožňuje zadat obory názvů pro typy, které budete používat ve svých výrazech. Podobně jako v případě **importu** nebo **použití** klíčových slov v Visual Basic a C# umožňuje zadání oborů názvů v Návrháři Imports jednoduše zadat název typu ve výrazu, nikoli plně kvalifikovaný název typu verze.

Návrhář importů reaguje na změny v uživatelském rozhraní a změny provedené při uložení pracovního postupu. Po uložení pracovního postupu lze obory názvů automaticky přidat do návrháře Imports. Patří mezi ně:

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
