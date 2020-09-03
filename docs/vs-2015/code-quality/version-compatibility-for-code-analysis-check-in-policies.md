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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609320"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatibilita verzí pro zásady vracení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pokud je nutné vyhodnotit a vytvořit zásady pro vrácení se změnami analýzy kódu pomocí různých verzí nástroje [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , je nutné znát rozdíly ve způsobu [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] a [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] vyhodnocení zásad vrácení se změnami.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Kompatibilita verzí pro vyhodnocení zásad vrácení se změnami

- Pokud jsou vyhodnocovány zásady vrácení se změnami analýzy kódu v nástroji [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , všechna pravidla, která existovala v, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ale neexistují v, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] jsou ignorována.

- Při vyhodnocení zásad vrácení se změnami analýzy kódu v nástroji jsou [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] všechna nová pravidla, která jsou výhradně pro, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignorována.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoruje všechna pravidla, která jsou určena sestaveními, která nerozpoznají.

- Pokud zásada pro vrácení se změnami analýzy kódu určuje sestavení pravidel, která [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nerozpoznají, zobrazí se zpráva.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Kompatibilita verzí pro vytváření zásad vracení se změnami

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí verze nástroje [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , nemůžete [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] ji upravovat pomocí verze. A také [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nemůže vyhodnotit zásady.

- Pokud jste vytvořili zásadu pro vrácení se změnami analýzy kódu pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , můžete použít [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] k její úpravě a zásadu lze také vyhodnotit pomocí [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Až zásadu upravíte pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v nástroji [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , nebudete už moct tyto zásady upravovat pomocí [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] v [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] může vyhodnotit zásady bez problémů s neodpovídajícími silnými názvy.

- Chcete-li vytvořit zásadu pro vrácení se změnami analýzy kódu s nastavením pravidla, které platí pro [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] a [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , musíte vytvořit zásadu v nástroji [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , provést všechny požadované změny a uložit zásadu. Pokud změny pravidel existují pouze v nástroji [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , můžete zásadu upravit a uložit v nástroji [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Až zásadu uložíte v nástroji [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , nebudete už moct měnit nastavení pravidel, která existují jenom v nástroji [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .
