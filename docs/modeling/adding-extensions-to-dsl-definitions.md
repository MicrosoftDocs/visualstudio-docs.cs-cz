---
title: Přidávání rozšíření do definicí DSL
description: Přečtěte si, jak vám rozšíření definice DSL umožňuje vytvořit balíček rozšíření pro jazyk specifický pro doménu (DSL).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 07057c24494a19d77bca872ad87adf20bb125252
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361141"
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
