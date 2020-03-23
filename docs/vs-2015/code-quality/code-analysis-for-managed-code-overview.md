---
title: Analýza kódu pro přehled spravovaného kódu | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "72610063"
---
# <a name="code-analysis-for-managed-code-overview"></a>Přehled Analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analýza kódu pro spravovaný kód analyzuje spravovaná sestavení a hlásí informace o sestaveních, jako je například porušení pravidel programování a návrhu stanovených v pokynech pro návrh rozhraní Microsoft .NET Framework.

 Analytický nástroj představuje kontroly, které provádí během analýzy jako varovné zprávy. Varovné zprávy identifikují všechny relevantní problémy s programováním a návrhem a pokud je to možné, poskytují informace o tom, jak problém vyřešit.

## <a name="ide-integrated-development-environment-integration"></a>Integrace IDE (integrované vývojové prostředí)
 Jako vývojář můžete spustit analýzu kódu v projektu automaticky nebo ji spustit ručně.

 Chcete-li spustit analýzu kódu při každém sestavení projektu, vyberte **povolit analýzu kódu při sestavení (definuje CODE_ANALYSIS konstanta)** na stránce vlastností projektu. Další informace naleznete v [tématu How to: Enable and Disable Automatic Code Analysis](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

 Chcete-li spustit analýzu kódu ručně v projektu, klepněte v nabídce **Analyzovat** na **tlačítko Spustit analýzu kódu na**_názvu_projektu_. Další informace naleznete v [tématu How to: Enable and Disable Automatic Code Analysis](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).

## <a name="rule-sets"></a>Sady pravidel
 Pravidla analýzy kódu pro spravovaný kód jsou seskupena do *sad pravidel*. Můžete použít jednu ze standardních sad pravidel společnosti Microsoft nebo můžete vytvořit vlastní sadu pravidel, která splní určitou potřebu. Další informace naleznete [v tématu Použití sad pravidel k pravidlům analýzy kódu skupiny](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).

## <a name="in-source-suppression"></a>V potlačení zdroje
 Často je užitečné označit, že upozornění není použitelné. To informuje vývojáře a další osoby, které by mohly zkontrolovat kód později, že upozornění bylo vyšetřeno a potom potlačeno nebo ignorováno.

 V Source Suppression of warnings je implementována prostřednictvím vlastních atributů. Chcete-li potlačit upozornění, `SuppressMessage` přidejte atribut do zdrojového kódu, jak je znázorněno v následujícím příkladu:

 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```

 Další informace naleznete v tématu [Potlačení upozornění pomocí suppressMessage Atribut](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).

## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Spustit analýzu kódu jako součást zásad vrácení se změnami
 Jako organizace můžete požadovat, aby všechny vrácení se změnami splňovaly určité zásady. Zejména se chcete ujistit, že dodržujete tyto zásady:

- V kódu, který byl zasazován se změnami, nebyly žádné chyby sestavení.

- Analýza kódu byla spuštěna jako součást nejnovějšího sestavení.

  Toho lze dosáhnout zadáním zásad vrácení se změnami. Další informace naleznete [v tématu Zlepšení kvality kódu pomocí zásad vrácení se změnami v týmových projektech](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).

## <a name="team-build-integration"></a>Integrace sestavení týmu
 Integrované funkce systému sestavení můžete použít ke spuštění nástroje analýzy jako součást procesu sestavení. Další informace naleznete [v tématu Sestavení aplikace](/azure/devops/pipelines/index).

## <a name="see-also"></a>Viz také
 [Použití sad pravidel k seskupit pravidla analýzy kódu:](../code-quality/using-rule-sets-to-group-code-analysis-rules.md) [Povolení a zakázání automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)
