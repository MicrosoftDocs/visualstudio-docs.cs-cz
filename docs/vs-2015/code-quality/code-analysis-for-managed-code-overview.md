---
title: Přehled analýzy kódu pro spravovaný kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: overview
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 33ab4a000fac75c51c32e8a6d37de62e006160b3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610063"
---
# <a name="code-analysis-for-managed-code-overview"></a>Přehled Analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analýza kódu pro spravovaný kód analyzuje spravovaná sestavení a sestavuje informace o sestaveních, jako jsou porušení pravidel programování a návrhu stanovených v pokynech pro návrh Microsoft .NET Framework.

 Nástroj pro analýzu představuje kontroly, které provádí během analýzy, jako varovné zprávy. Varovné zprávy identifikují relevantní problémy s programováním a návrhem a, pokud je to možné, poskytují informace o tom, jak tento problém vyřešit.

## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)
 Jako vývojář můžete spustit analýzu kódu na projektu automaticky nebo ho můžete spustit ručně.

 Chcete-li spustit analýzu kódu při každém sestavení projektu, vyberte možnost **Povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta)** na stránce vlastností projektu. Další informace najdete v tématu [Postup: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Chcete-li spustit analýzu kódu ručně v projektu, v nabídce **analyzovat** klikněte na možnost **Spustit analýzu kódu v**_ProjectName_. Další informace najdete v tématu [Postup: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Sady pravidel
 Pravidla analýzy kódu pro spravovaný kód jsou seskupena do *sad pravidel*. Můžete použít jednu ze standardních sad pravidel společnosti Microsoft, nebo můžete vytvořit vlastní sadu pravidel, která bude splňovat konkrétní potřebnou potřebu. Další informace najdete v tématu [použití sad pravidel k seskupení pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>Při potlačení zdroje
 Často je užitečné indikovat, že upozornění není k dispozici. Tím se vývojář informuje a další lidé, kteří si mohou kód později projít, že bylo prověřeno upozornění a pak potlačí nebo ignoruje.

 Ve zdrojovém potlačení upozornění je implementováno prostřednictvím vlastních atributů. Chcete-li potlačit upozornění, přidejte atribut `SuppressMessage` do zdrojového kódu, jak je znázorněno v následujícím příkladu:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Další informace naleznete v tématu [potlačení upozornění pomocí atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Spustit analýzu kódu jako součást zásady vracení se změnami
 Jako organizace budete možná chtít vyžadovat, aby všechna vrácení se změnami splňovala určité zásady. Zejména se chcete ujistit, že dodržujete tyto zásady:

- V kódu se nevrátily žádné chyby buildu.

- Analýza kódu byla spuštěna jako součást nejnovějšího buildu.

  To můžete provést zadáním zásad vracení se změnami. Další informace naleznete v tématu [zvyšování kvality kódu pomocí zásad vracení zpět se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integrace sestavení týmu
 Můžete použít integrované funkce systému sestavení ke spuštění nástroje pro analýzu jako součást procesu sestavení. Další informace naleznete v tématu [sestavování aplikace](/azure/devops/pipelines/index).

## <a name="see-also"></a>Viz také
 [Použití sad pravidel k seskupení pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [Postupy: povolení a zákaz automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
