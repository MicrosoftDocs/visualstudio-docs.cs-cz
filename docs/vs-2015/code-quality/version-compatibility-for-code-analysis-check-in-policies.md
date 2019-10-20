---
title: Kompatibilita verzí pro zásady vracení zpět se změnami analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609320"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud je nutné vyhodnotit a vytvořit zásady pro vrácení se změnami analýzy kódu pomocí různých verzí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], je nutné znát rozdíly ve způsobu, jakým [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] a [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] zásady vracení se změnami vyhodnotit.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatibilita verzí pro vyhodnocení zásad vrácení se změnami

- Když jsou v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] vyhodnocovány zásady vrácení se změnami analýzy kódu, všechna pravidla, která existovala v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], ale v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] neexistují, se ignorují.

- Když jsou v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] vyhodnocovány zásady vrácení se změnami analýzy kódu, všechna nová pravidla, která jsou výhradně pro [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], se ignorují.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignorují všechna pravidla, která jsou určena sestaveními, která nerozpoznají.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, která [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nerozpoznají, zobrazí se zpráva.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatibilita verzí pro vytváření zásad vracení se změnami

- Pokud jste vytvořili zásadu vrácení se změnami analýzy kódu pomocí [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] verze [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], nemůžete k její úpravě použít [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] verzi [!INCLUDE[esprtfc](../includes/esprtfc-md.md)]. @No__t_0 také nemůže vyhodnotit zásady.

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], můžete ji upravit pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] a zásadu je také možné vyhodnotit pomocí [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Když zásadu upravíte pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], nebudete už moct tuto zásadu upravovat pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] může vyhodnotit zásady bez problémů s neodpovídajícími silnými názvy.

- Chcete-li vytvořit zásadu pro vrácení se změnami analýzy kódu s nastavením pravidla, které platí pro [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] i [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], je nutné vytvořit zásadu v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], provést všechny změny a uložit zásadu. Pokud změny pravidel existují pouze v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], upravíte a uložíte zásadu v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].

     Až zásadu uložíte v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], nebudete už moct měnit nastavení pravidel, která existují jenom v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)].
