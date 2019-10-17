---
title: Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c233d174922c0853d771356e0b68185c51c368ea
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72448732"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu

Pokud je nutné vyhodnotit a vytvořit zásady pro vrácení se změnami analýzy kódu pomocí různých verzí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], je nutné znát rozdíly ve způsobu, jakým [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vyhodnotit zásady vrácení se změnami.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatibilita verzí pro vyhodnocení zásad vrácení se změnami

- Pokud jsou zásady vrácení se změnami analýzy kódu vyhodnocovány v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], všechna pravidla, která existovala v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], ale neexistují v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], se ignorují.

- Pokud jsou vyhodnoceny zásady vrácení se změnami analýzy kódu v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], budou ignorována všechna nová pravidla, která jsou výhradně [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoruje všechna pravidla, která jsou určena sestaveními, která nerozpoznají.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, která [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] rozpoznána, zobrazí se zpráva.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatibilita verzí pro vytváření zásad vracení se změnami

- Pokud jste vytvořili zásadu vrácení se změnami analýzy kódu pomocí [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verze [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], nemůžete ji upravovat pomocí verze [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]. @No__t-0 také nemůže vyhodnotit zásady.

- Pokud jste vytvořili zásadu vrácení se změnami analýzy kódu pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], můžete ji upravit pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] a zásadu je také možné vyhodnotit [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Když zásadu upravíte pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nebudete už moct tuto zásadu upravovat pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] může vyhodnotit zásady bez problémů s neodpovídajícími silnými názvy.

- Chcete-li vytvořit zásadu pro vrácení se změnami analýzy kódu s nastavením pravidla, která platí pro [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] i [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], je nutné vytvořit zásadu v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], provést všechny změny a uložit zásadu. Pokud změny pravidel existují pouze v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], upravíte a uložíte zásadu v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Až zásadu uložíte v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nebudete už moct měnit nastavení pravidel, která existují jenom v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
