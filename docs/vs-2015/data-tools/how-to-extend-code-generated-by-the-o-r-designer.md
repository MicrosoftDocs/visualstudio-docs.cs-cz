---
title: 'Postupy: rozšiřování kódu generovaného návrhářem O-R | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665951"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Postupy: Rozšíření kódu vygenerovaného Návrhářem relací objektů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kód generovaný pomocí [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] je znovu vygenerován při změnách tříd entit a dalších objektů na návrhové ploše. Z důvodu tohoto opětovného generování kódu je kód, který přidáte do generovaného kódu, obvykle přepsán, když Návrhář znovu vygeneruje kód. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Poskytuje možnost generovat soubory částečné třídy, ve kterých můžete přidat kód, který nebude přepsán. Jedním z příkladů Přidání vlastního kódu do kódu generovaného nástrojem [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] je přidání ověření dat do tříd LINQ to SQL (entita). Informace najdete v tématu [Postup: Přidání ověřování do tříd entit](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Přidání kódu do třídy entity

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Chcete-li vytvořit částečnou třídu a přidat kód do třídy entity

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Poklikejte na soubor **. dbml** v **Průzkumník řešení** / **Průzkumník databáze**.)

2. V klikněte [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] pravým tlačítkem na třídu, pro kterou chcete přidat ověřování, a pak klikněte na **Zobrazit kód**.

     Otevře se Editor kódu s částečnou třídou pro vybranou třídu entity.

3. Přidejte svůj kód v deklaraci částečné třídy pro třídu entity.

## <a name="adding-code-to-a-datacontext"></a>Přidání kódu do kontextu DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Chcete-li vytvořit částečnou třídu a přidat kód do kontextu DataContext

1. Otevřete nebo vytvořte nový soubor LINQ to SQLch tříd (soubor **. dbml** ) v [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . (Poklikejte na soubor **. dbml** v **Průzkumník řešení** / **Průzkumník databáze**.)

2. V klikněte [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] pravým tlačítkem myši na prázdnou oblast návrháře a pak klikněte na **Zobrazit kód**.

     Editor kódu se otevře s částečnou třídou pro DataContext.

3. Přidejte svůj kód v deklaraci částečné třídy pro DataContext.

## <a name="see-also"></a>Viz také
 [LINQ to SQL Tools v aplikaci Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [– návod: vytváření LINQ to SQL tříd (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [návodu: Přidání ověřování do tříd entit](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)
