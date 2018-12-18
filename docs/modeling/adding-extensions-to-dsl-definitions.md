---
title: Přidávání rozšíření do definicí DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: dc764df3037baeba36666ce896549018d86c2a21
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947531"
---
# <a name="add-extensions-to-dsl-definitions"></a>Přidejte rozšíření do definice DSL

Rozšíření definice DSL umožňuje vytvořit balíček rozšíření pro jazyk, specifické pro doménu (DSL). Přípony DSL, který je obsažen ve Visual Studio integrace rozšíření (VSIX), lze nainstalovat na počítači uživatele stejným způsobem jako DSL. Další funkce lze dynamicky povolit a zakázat v době běhu. DSL, linky nemusí být explicitně určen pro rozšíření a rozšíření nelze navrhnout později, nebo třetích stran, beze změny rozšířené DSL.

Rozšíření DSL může zahrnovat následující funkce:

-   Vlastnosti elementů modelu a prezentace

-   Dekoratéry pro konektory a obrazců

-   Třídy, relace, tvarů a konektory

-   Omezení ověřování

-   Položky panelu nástrojů a karty

Uživatel rozšířené DSL můžete vytvořit a uložit model, který obsahuje instance dalších funkcí. Model můžete přečíst další uživatelé, kteří mají nainstalované příslušná rozšíření. Uživatelé, kteří nejsou nainstalované rozšíření nelze použít další funkce, ale můžete aktualizovat a uložit model bez ztráty dalších funkcí.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Viz také

- [Příspěvky blogu související](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)
