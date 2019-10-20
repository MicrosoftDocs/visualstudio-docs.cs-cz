---
title: Vytváření a používání zásad vrácení se změnami analýzy kódu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: 3fa5a849-e05f-4e31-8ba3-b014c889d94d
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8e31ff799edc93d250eeeab57b349873a63ecf14
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667717"
---
# <a name="creating-and-using-code-analysis-check-in-policies"></a>Vytváření a používání zásad vrácení se změnami Analýzy kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při použití Správa verzí Team Foundation (TFVC) můžete vytvořit zásadu pro vrácení se změnami analýzy kódu pro .NET Framework a nativní projekty kódu (C/C++) v týmovém projektu. Můžete použít zásadu vrácení se změnami analýzy kódu pro kontrolu a zlepšení kvality kódu, který je vrácen do základu kódu.

 Zásada se dokončí, když je místní sestavení aktuální a na nejnovější zdrojové soubory se spustí analýza kódu. Minimálně pravidla analýzy kódu, která jsou povolená v projektu kódu, musí obsahovat stejná pravidla jako ta, která jsou definovaná v zásadách vrácení se změnami týmového projektu. Pravidla, která byla zadána jako chyby v nastavení týmového projektu, musí být také zadána jako chyby v projektu kódu.

> [!IMPORTANT]
> Zásady vrácení se změnami analýzy kódu nelze použít u projektů webu. Mohou být aplikovány na projekty webových aplikací.

 Zásady vrácení se změnami analýzy kódu se vytvářejí pomocí nastavení týmového projektu [!INCLUDE[esprscc](../includes/esprscc-md.md)]. Zásady vrácení se změnami jsou zadány a vynutily pro týmový projekt, ale běhy analýzy kódu jsou nakonfigurovány a spuštěny pro jednotlivé projekty kódu na místních vývojových počítačích. Tato část popisuje, jak určit zásady analýzy kódu pro vrácení se změnami pro týmový projekt a jak implementovat vlastní zásady analýzy kódu pro spravovaný kód.

## <a name="in-this-section"></a>V tomto oddílu
 [Postupy: vytváření nebo aktualizace standardních zásad vracení se změnami analýzy kódu](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md) Vysvětluje kroky, které slouží k nastavení a úpravě zásad analýzy kódu pro týmový projekt.

 [Implementace vlastních zásad vrácení se změnami pro spravovaný kód](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md) Vysvětluje kroky, které použijete k vytvoření vlastní sady pravidel pro zásady vracení se změnami týmového projektu a k synchronizaci projektů kódu týmového projektu se zásadou vrácení se změnami.

 [Kompatibilita verzí pro zásady vracení se změnami analýzy kódu](../code-quality/version-compatibility-for-code-analysis-check-in-policies.md) Vysvětluje problémy s kompatibilitou analýzy kódu při vracení se změnami mezi verzemi [!INCLUDE[vstsLong](../includes/vstslong-md.md)].

 [Postupy: přizpůsobení slovníku analýzy kódu](../code-quality/how-to-customize-the-code-analysis-dictionary.md) Vysvětluje, jak přidat slova a tokeny do slovníku, na který je odkazováno v pravidla vytváření názvů nástroje Analýza kódu.

## <a name="related-sections"></a>Související oddíly
 [Nastavení a vymáhání bran kvality](https://msdn.microsoft.com/library/bdc5666e-6cf0-45b2-a0a1-133c3f61e852)

 [Zvýšení kvality kódu použitím zásad vracení se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md)
