---
title: Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4757b3a105ff02a92944d9b45e645e2c63a8b81c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587157"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu

Pokud je nutné vyhodnotit a vytvořit zásady pro vrácení se změnami analýzy kódu pomocí různých verzí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], je nutné znát rozdíly ve způsobu, jakým [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] zásady vracení se změnami vyhodnotit.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatibilita verzí pro vyhodnocení zásad vrácení se změnami

- Když jsou v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]vyhodnocovány zásady vrácení se změnami analýzy kódu, všechna pravidla, která existovala v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], ale v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] neexistují, se ignorují.

- Když jsou v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]vyhodnocovány zásady vrácení se změnami analýzy kódu, všechna nová pravidla, která jsou výhradně pro [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], se ignorují.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignorují všechna pravidla, která jsou určena sestaveními, která nerozpoznají.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, která [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nerozpoznají, zobrazí se zpráva.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatibilita verzí pro vytváření zásad vracení se změnami

- Pokud jste vytvořili zásadu vrácení se změnami analýzy kódu pomocí [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] verze [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], nemůžete k její úpravě použít [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] verzi [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] také nemůže vyhodnotit zásady.

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], můžete ji upravit pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] a zásadu je také možné vyhodnotit pomocí [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Když zásadu upravíte pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nebudete už moct tuto zásadu upravovat pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] může vyhodnotit zásady bez problémů s neodpovídajícími silnými názvy.

- Chcete-li vytvořit zásadu pro vrácení se změnami analýzy kódu s nastavením pravidla, které platí pro [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] i [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], je nutné vytvořit zásadu v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], provést všechny změny a uložit zásadu. Pokud změny pravidel existují pouze v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], upravíte a uložíte zásadu v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Až zásadu uložíte v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], nebudete už moct měnit nastavení pravidel, která existují jenom v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
