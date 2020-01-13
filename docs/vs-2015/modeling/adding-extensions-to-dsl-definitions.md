---
title: Přidávání rozšíření do definic DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919061"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Přidávání rozšíření do definicí DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Rozšíření definice DSL umožňuje vytvořit balíček rozšíření pro jazyk specifický pro doménu (DSL). Přípona DSL, která je obsažena v rozšíření integrace sady Visual Studio (VSIX), může být nainstalována v počítači uživatele stejným způsobem jako DSL. Další funkce lze v době běhu dynamicky povolit a zakázat. DSL nemusí být explicitně navržené pro rozšíření a rozšíření může být navrženo později nebo třetími stranami bez změny rozšířené DSL.

 Další funkce mohou zahrnovat následující:

- Vlastnosti pro model a prezentační prvky

- Dekoratéry pro obrazce a konektory

- Třídy, vztahy, obrazce a konektory

- Omezení ověřování

- Položky a karty nástrojů

  Uživatel rozšířené DSL může vytvořit a uložit model, který obsahuje instance dalších funkcí, a číst ho jiní uživatelé, kteří si nainstalovali odpovídající rozšíření. Uživatelé, kteří rozšíření nenainstalovali, nemohou používat další funkce, ale mohou aktualizovat a uložit model bez ztráty dalších funkcí.

  Vzorový kód a další informace o této funkci najdete na webu [sady Visual Studio pro vizualizaci a modelování sady SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) .

## <a name="see-also"></a>Viz také
 [Sada SDK pro vizualizaci a modelování sady Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
