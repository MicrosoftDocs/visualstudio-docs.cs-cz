---
title: Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu
ms.date: 11/04/2016
description: Přečtěte si, jak Team System 2008 Team Foundation Server a Team Foundation Server 2010 vyhodnotit zásady vrácení se změnami sady Visual Studio různě.
ms.custom: SEO-VS-2020
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 24a97e9175e75d8018aff269066f13a796e1cf64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867669"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu

Pokud je nutné vyhodnotit a vytvořit zásady pro vrácení se změnami analýzy kódu pomocí různých verzí nástroje [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , je nutné znát rozdíly ve způsobu [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] a [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] vyhodnocení zásad vrácení se změnami.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatibilita verzí pro vyhodnocení Check-Inch zásad

- Pokud jsou vyhodnocovány zásady vrácení se změnami analýzy kódu v nástroji [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , všechna pravidla, která existovala v, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ale neexistují v, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] jsou ignorována.

- Při vyhodnocení zásad vrácení se změnami analýzy kódu v nástroji jsou [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] všechna nová pravidla, která jsou výhradně pro, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignorována.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoruje všechna pravidla, která jsou určena sestaveními, která nerozpoznají.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, která [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nerozpoznají, zobrazí se zpráva.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatibilita verzí pro vytváření Check-Inch zásad

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí verze nástroje [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , nemůžete [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] ji upravovat pomocí verze. A také [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nemůže vyhodnotit zásady.

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , můžete použít [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] k její úpravě a zásadu lze také vyhodnotit pomocí [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Až zásadu upravíte pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v nástroji [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , nebudete už moct tyto zásady upravovat pomocí [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] v [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] může vyhodnotit zásady bez problémů s neodpovídajícími silnými názvy.

- Chcete-li vytvořit zásadu pro vrácení se změnami analýzy kódu s nastavením pravidla, které platí pro [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] a [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , musíte vytvořit zásadu v nástroji [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , provést všechny požadované změny a uložit zásadu. Pokud změny pravidel existují pouze v nástroji [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , můžete zásadu upravit a uložit v nástroji [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Až zásadu uložíte v nástroji [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , nebudete už moct měnit nastavení pravidel, která existují jenom v nástroji [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
