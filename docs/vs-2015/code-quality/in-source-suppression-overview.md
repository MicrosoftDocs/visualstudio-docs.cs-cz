---
title: Přehled potlačování ve zdroji | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 844681d079e5565aab9eceadb73f7d8a61cbb2c6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209037"
---
# <a name="in-source-suppression-overview"></a>Přehled potlačování ve zdroji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potlačení v zdroje je možnost potlačit nebo ignorovat porušení zásad analýzy kódu ve spravovaném kódu tak, že přidáte **SuppressMessage** atribut segmentů kódu, které způsobují porušení zásad. **SuppressMessage** atribut je podmíněný atribut, který je součástí metadata IL sestavení spravovaného kódu jenom v případě, že je definován symbol kompilace CODE_ANALYSIS v době kompilace.  
  
 V jazyce C + +/ CLI, použijte makra CA_SUPPRESS_MESSAGE nebo CA_GLOBAL_SUPPRESS_MESSAGE v souboru hlaviček, chcete-li přidat atribut.  
  
 Zabránit potlačení v zdroje metadat přesouvání omylem byste neměli používat potlačení v zdroje u sestavení pro vydání. Vzhledem k zpracování potlačení-source může být také snížený výkon vaší aplikace zahrnutím potlačení v zdroje metadat.  
  
> [!NOTE]
>  Není nutné ručně kód tyto atributy sami. Další informace najdete v tématu [postupy: potlačení upozornění použitím položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Položka nabídky není k dispozici pro kód C++.  
  
## <a name="suppressmessage-attribute"></a>Atributu SuppressMessage  
 Když kliknete pravým tlačítkem na upozornění analýzy kódu v **seznam chyb** a potom klikněte na tlačítko **potlačení zpráv**, **SuppressMessage** je ve vašem kódu nebo na Přidat atribut projektový soubor globálního potlačení.  
  
 **SuppressMessage** atribut má následující formát:  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```csharp  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 [C++]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 kde:  
  
-   **Pravidlo kategorie** – kategorie, ve které je definováno pravidlo. Další informace o kategoriích pravidla analýzy kódu, naleznete v tématu [spravovaného kódu upozornění analýzy kódu pro](../code-quality/code-analysis-for-managed-code-warnings.md).  
  
-   **Id pravidla** -identifikátor pravidla. Podpora zahrnuje jak krátký a dlouhý název identifikátor pravidla. Krátký název je CAXXXX; dlouhý název je CAXXXX:FriendlyTypeName.  
  
-   **Odůvodnění** – text, který se používá k dokumentu důvod pro potlačení zprávy.  
  
-   **Id zprávy** – jedinečný identifikátor pro každou zprávu problém.  
  
-   **Obor** – cíl, na kterém je potlačeno upozornění. Pokud cíl není zadán, je nastavena na cíl atributu. Podporované obory, patří:  
  
    -   Modul  
  
    -   Obor názvů  
  
    -   Prostředek  
  
    -   Typ  
  
    -   Člen  
  
-   **Cíl** – identifikátor, který se používá k určení cíle, na kterém je potlačeno upozornění. Musí obsahovat položky plně kvalifikovaný název.  
  
## <a name="suppressmessage-usage"></a>SuppressMessage využití  
 Upozornění analýzy kódu jsou potlačeny na úrovni, do které instanci **SuppressMessage** atribut se používá. Účelem tohoto objektu je úzce spárovat informace o potlačení kódu kde dojde k porušení zásady.  
  
 Obecný tvar potlačení obsahuje kategorie pravidel a identifikátor pravidla, která obsahuje reprezentaci volitelné čitelný název pravidla. Například  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 Pokud jsou kvůli výkonu přísné pro minimalizaci potlačení v zdroje metadat, samotný název pravidla může zůstat navýšení kapacity. Kategorie pravidel a jeho ID pravidla společně tvoří pravidlo dostatečně jedinečný identifikátor. Například  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 Tento formát se nedoporučuje kvůli problémům s udržovatelnost.  
  
## <a name="suppressing-multiple-violations-within-a-method-body"></a>Potlačení více narušení v těle metody  
 Atributy lze použít pouze na metodu a nemůže být vložený, uvnitř těla metody. Můžete však zadat identifikátor jako ID zprávy k rozlišení více výskytů typů je porušení pravidel v rámci metody.  
  
 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]  
  
## <a name="generated-code"></a>Generovaný kód  
 Spravovaný kód kompilátory a některé nástroje třetích stran generování kódu pro usnadnění vývoje rychlý kód. Kód generovaný kompilátorem, který se zobrazí ve zdrojových souborech obvykle označené **GeneratedCodeAttribute** atribut.  
  
 Můžete zvolit, jestli se má potlačit upozornění analýzy kódu a chyby pro vygenerovaný kód. Informace o tom, jak potlačit takové upozornění a chyby najdete v tématu [postupy: potlačení upozornění pro kód generovaný](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).  
  
 Všimněte si, že analýza kódu ignoruje **GeneratedCodeAttribute** při použití na celé sestavení nebo jeden parametr. Těmito situacemi dojít jen zřídka.  
  
## <a name="global-level-suppressions"></a>Potlačení na globální úrovni  
 Nástroj pro analýzu spravovaného kódu prozkoumá **SuppressMessage** atributy, které jsou použity na úrovni sestavení, modulu, typu, člen nebo parametr. Je také vyvoláno porušení proti prostředky a obory názvů. Tato porušení se musí použít na globální úrovni a jsou obor a cílem. Například následující zpráva potlačí narušení obor názvů:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  Při potlačení upozornění se obor názvů, potlačí případná upozornění pro obor názvů, samotného. Upozornění s typy v rámci oboru názvů je nepotlačuje.  
  
 Žádné potlačení lze vyjádřit zadáním výslovného oboru. Tyto potlačení musí být aktivní na globální úrovni. Potlačení na úrovni člena nelze zadat pomocí upravení typu.  
  
 Potlačení na globální úrovni jsou jediným způsobem, jak potlačí zobrazování zpráv, které odkazují na kód generovaný kompilátorem, které nejsou namapované na výslovně zadaný uživatelský zdroj. Například následující kód potlačí porušení proti vyslaném kompilátor konstruktor:  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  Target vždy obsahuje plně kvalifikovaný název.  
  
## <a name="global-suppression-file"></a>Soubor globálního potlačení  
 Soubor globálního potlačení udržuje potlačení, které jsou potlačení na globální úrovni nebo potlačení, u kterých není cíl. Například pro porušení úrovně sestavení jsou uložena v tomto souboru. Kromě toho některé technologie ASP.NET jsou uložena v tomto souboru vzhledem k tomu, že nastavení na úrovni projektu nejsou k dispozici pro kódu na pozadí formuláře. Globální potlačení je vytvořen a přidán do projektu poprvé, kterou jste vybrali **v souboru potlačení projektu** možnost **potlačení zpráv** příkazu v okně Seznam chyb. Další informace najdete v tématu [postupy: potlačení upozornění použitím položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Diagnostics.CodeAnalysis>



