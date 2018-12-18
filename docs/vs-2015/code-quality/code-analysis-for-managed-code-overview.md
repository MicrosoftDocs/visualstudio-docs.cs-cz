---
title: Analýza kódu pro spravovaný kód přehled | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.projectpropertypages.codeanalysis
helpviewer_keywords:
- code analysis, managed code
- managed code, code analysis
ms.assetid: 12ec0dab-46a4-43d8-984a-440730ef37a9
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 5024e03fc48a4055cabba1e91dac42d61d6de805
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389089"
---
# <a name="code-analysis-for-managed-code-overview"></a>Přehled Analýzy kódu pro spravovaný kód
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Analýza kódu pro spravovaný kód analyzuje spravovaná sestavení a hlásí informace o sestaveních, jako jsou porušení programování a návrhu pravidel stanoví pokyny pro návrh rozhraní Microsoft .NET Framework.  
  
 Analytický nástroj představuje kontroly, které provádí během analýzy jako upozornění. Upozornění identifikují jakékoli relevantní problémy programování a návrhu a kdy je možné, poskytují informace o tom, jak tento problém vyřešit.  
  
## <a name="ide-integrated-development-environment-integration"></a>Integrace integrovaného vývojového prostředí (IDE)  
 Jako vývojář můžete spustit analýzu kódu na projektu automaticky nebo ji můžete spustit ručně.  
  
 Chcete-li spustit analýzu kódu při každém sestavení projektu, je vybrat **povolit analýzu kódu na sestavení (definuje konstantu CODE_ANALYSIS)** na stránce vlastností projektu. Další informace najdete v tématu [postupy: povolení a zakázání automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
 Pro ruční spuštění analýzy kódu na projektu, na **analyzovat** nabídky, klikněte na tlačítko **spustit analýzu kódu na**_ProjectName_. Další informace najdete v tématu [postupy: povolení a zakázání automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md).  
  
## <a name="rule-sets"></a>Sady pravidel  
 Pravidla analýzy kódu pro spravovaný kód jsou seskupena do *sad pravidel*. Můžete použít jednu ze sad standardních pravidel společnosti Microsoft, nebo můžete vytvořit vlastní sadu pravidel, která za určitým účelem. Další informace najdete v tématu [pomocí sad pravidel k seskupování pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md).  
  
## <a name="in-source-suppression"></a>Při potlačení zdroje  
 Často je užitečné označit, že varování není použitelné. To upozorní vývojáře a ostatní uživatele, kteří později, může zkontrolovat kód, že upozornění byla prozkoumat a potlačeno nebo ignorováno.  
  
 Ve zdrojové potlačení varování implementováno skrze vlastní atributy. Pro potlačení varování je zapotřebí, přidejte atribut `SuppressMessage` ke zdrojovému kódu, jak je znázorněno v následujícím příkladu:  
  
 ```csharp
 [System.Diagnostics.CodeAnalysis.SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]
 Public class MyClass
 {
     // code
 }
 ```
  
 Další informace najdete v tématu [potlačit upozornění s použitím atributu SuppressMessage](../code-quality/suppress-warnings-by-using-the-suppressmessage-attribute.md).  
  
## <a name="run-code-analysis-as-part-of-check-in-policy"></a>Spustit analýzu kódu jako součást zásady vrácení se změnami  
 Jako organizace můžete vyžadovat, aby všechna vrácení se změnami splňovala určitá kritéria. Zejména budete chtít Ujistěte se, že jsou dodržovány tyto zásady:  
  
- Nedošlo k chybám sestavení v kódu se změnami.  
  
- Analýza kódu byla spuštěna jako součást nejnovějšího sestavení.  
  
  Toho lze dosáhnout zadáním zásad vrácení se změnami. Další informace najdete v tématu [zlepšení kvality kódu pomocí zásady vrácení se změnami týmového projektu](../code-quality/enhancing-code-quality-with-team-project-check-in-policies.md).  
  
## <a name="team-build-integration"></a>Integrace týmového sestavení  
 Chcete-li spustit nástroj pro analýzu jako součást procesu sestavení můžete použít integrované funkce systému sestavení. Další informace najdete v tématu [sestavte aplikaci](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
## <a name="see-also"></a>Viz také  
 [Použití sad pravidel k seskupování pravidel analýzy kódu](../code-quality/using-rule-sets-to-group-code-analysis-rules.md)   
 [Postupy: Povolení a zakázání automatické analýzy kódu](../code-quality/how-to-enable-and-disable-automatic-code-analysis-for-managed-code.md)



