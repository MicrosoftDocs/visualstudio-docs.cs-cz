---
title: Přidávání rozšíření do definicí DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3e44c79783479c46247e4026788725d6ae16da7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747657"
---
# <a name="add-extensions-to-dsl-definitions"></a>Přidání rozšíření do definic DSL

Rozšíření definice DSL umožňuje vytvořit balíček rozšíření pro jazyk specifický pro doménu (DSL). Přípona DSL, která je obsažena v rozšíření integrace sady Visual Studio (VSIX), může být nainstalována v počítači uživatele stejným způsobem jako DSL. Další funkce lze v době běhu dynamicky povolit a zakázat. DSL nemusí být explicitně navržené pro rozšíření a rozšíření je možné navrhnout později nebo třetí strany, aniž by změnili rozšířenou DSL.

Rozšíření DSL můžou zahrnovat následující funkce:

- Vlastnosti pro model a prezentační prvky

- Dekoratéry pro obrazce a konektory

- Třídy, vztahy, obrazce a konektory

- Omezení ověřování

- Položky a karty nástrojů

Uživatel rozšířené DSL může vytvořit a uložit model, který obsahuje instance dalších funkcí. Model můžou číst jiní uživatelé, kteří si nainstalovali odpovídající rozšíření. Uživatelé, kteří rozšíření nenainstalovali, nemohou používat další funkce, ale mohou aktualizovat a uložit model bez ztráty dalších funkcí.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Viz také:

- [Související blogové příspěvky](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
