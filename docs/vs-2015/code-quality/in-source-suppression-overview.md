---
title: V přehledu potlačení zdroje | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- source suppression, code analysis
- code analysis, source suppression
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 63d405b0e62735c0c1e3d7bb716ea2db29bc19fe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651578"
---
# <a name="in-source-suppression-overview"></a>Přehled potlačování ve zdroji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Potlačení ve zdroji je schopnost potlačit nebo ignorovat porušení analýzy kódu ve spravovaném kódu přidáním atributu **SuppressMessage** do segmentů kódu, které způsobují porušení. Atribut **SuppressMessage** je podmíněný atribut, který je obsažen v metadatech Il sestavení spravovaného kódu pouze v případě, že je v době kompilace definován symbol kompilace CODE_ANALYSIS.

 V C++/CLI použijte makra CA_SUPPRESS_MESSAGE nebo CA_GLOBAL_SUPPRESS_MESSAGE v hlavičkovém souboru, chcete-li přidat atribut.

 V sestavách vydaných verzí byste neměli používat potlačení ve zdrojovém kódu, abyste zabránili nechtěnému přenosu metadat potlačení. Vzhledem k nákladům na zpracování ve zdrojovém potlačení můžete také snížit výkon aplikace tím, že zahrnete metadata potlačení ve zdroji.

> [!NOTE]
> Tyto atributy nemusíte sami nakódovat sami. Další informace naleznete v tématu [How to: potlačení upozornění pomocí položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md). Položka nabídky není pro C++ kód k dispozici.

## <a name="suppressmessage-attribute"></a>SuppressMessage – atribut
 Když kliknete pravým tlačítkem na upozornění analýzy kódu v **Seznam chyb** a potom kliknete na **Potlačit zprávy**, přidá se do kódu nebo do globálního souboru potlačení projektu atribut **SuppressMessage** .

 Atribut **SuppressMessage** má následující formát:

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

 ,

- **Kategorie pravidla** – kategorie, ve které je definováno pravidlo. Další informace o kategoriích pravidla analýzy kódu najdete v tématu [upozornění analýzy kódu pro spravovaný kód](../code-quality/code-analysis-for-managed-code-warnings.md).

- **ID pravidla** – identifikátor pravidla. Podpora zahrnuje krátký i dlouhý název identifikátoru pravidla. Krátký název je CAXXXX; dlouhé jméno je CAXXXX: FriendlyTypeName.

- **Odůvodnění** – text, který se používá k dokumentaci důvodu pro potlačení zprávy.

- **ID zprávy** – jedinečný identifikátor problému pro každou zprávu.

- **Rozsah** – cíl, na kterém je upozornění potlačeno. Pokud není cíl zadán, je nastaven na cíl atributu. Mezi podporované obory patří následující:

  - Modul

  - Obor názvů

  - Partner

  - Typ

  - Člen

- **Target** – identifikátor, který se používá k určení cíle, na kterém je upozornění potlačeno. Musí obsahovat plně kvalifikovaný název položky.

## <a name="suppressmessage-usage"></a>Využití SuppressMessage
 Upozornění analýzy kódu jsou potlačena na úrovni, na kterou je použita instance atributu **SuppressMessage** . Účelem tohoto je pevně spojit informace o potlačení s kódem, kde dojde k porušení.

 Obecná forma potlačení zahrnuje kategorii pravidla a identifikátor pravidla, který obsahuje nepovinné uživatelsky čitelné reprezentace názvu pravidla. Například

 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`

 Pokud existují přísné důvody pro výkon pro minimalizaci v metadatech potlačení zdroje, může být název samotného pravidla vynechán. Kategorie pravidla a ID pravidla společně tvoří dostatečně jedinečný identifikátor pravidla. Například

 `[SuppressMessage("Microsoft.Design", "CA1039")]`

 Tento formát se nedoporučuje kvůli problémům s udržovatelnosti.

## <a name="suppressing-multiple-violations-within-a-method-body"></a>Potlačení více porušení v rámci těla metody
 Atributy lze použít pouze pro metodu a nelze je vložit do těla metody. Můžete však určit identifikátor jako ID zprávy pro odlišení více výskytů porušení v rámci metody.

 [!code-cpp[InSourceSuppression#1](../snippets/cpp/VS_Snippets_CodeAnalysis/InSourceSuppression/cpp/insourcesuppression.cpp#1)]
 [!code-csharp[InSourceSuppression#1](../snippets/csharp/VS_Snippets_CodeAnalysis/InSourceSuppression/cs/InSourceSuppression.cs#1)]
 [!code-vb[InSourceSuppression#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/InSourceSuppression/vb/InSourceSuppression.vb#1)]

## <a name="generated-code"></a>Generovaný kód
 Kompilátory spravovaného kódu a některé nástroje třetích stran generují kód pro usnadnění rychlého vývoje kódu. Kód generovaný kompilátorem, který se zobrazí ve zdrojových souborech, je obvykle označen atributem **GeneratedCodeAttribute** .

 Můžete zvolit, zda chcete potlačit upozornění a chyby analýzy kódu pro vygenerovaný kód. Informace o tom, jak potlačit taková upozornění a chyby, naleznete v tématu [How to: potlačit upozornění pro generovaný kód](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md).

 Všimněte si, že analýza kódu ignoruje **GeneratedCodeAttribute** při použití na celé sestavení nebo na jeden parametr. K těmto situacím dochází zřídka.

## <a name="global-level-suppressions"></a>Potlačení na globální úrovni
 Nástroj pro analýzu spravovaného kódu prověřuje atributy **SuppressMessage** , které jsou aplikovány na úrovni sestavení, modulu, typu, člena nebo parametru. Také se aktivují narušení proti prostředkům a oborům názvů. Tato porušení musí být použita na globální úrovni a mají rozsah a cíl. Například následující zpráva potlačuje porušení oboru názvů:

 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`

> [!NOTE]
> Potlačíte-li upozornění s oborem názvů, potlačí se upozornění proti samotnému oboru názvů. Potlačí upozornění na typy v rámci oboru názvů.

 Jakékoli potlačení lze vyjádřit zadáním explicitního oboru. Tato potlačení musí být živá na globální úrovni. Nemůžete zadat potlačení na úrovni člena upravení typem.

 Potlačení globální úrovně jsou jediným způsobem, jak potlačit zprávy, které odkazují na kód generovaný kompilátorem, který není namapován na explicitně zadaný zdroj uživatele. Například následující kód potlačí porušení proti konstruktoru generovanému kompilátorem:

 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`

> [!NOTE]
> Cíl vždy obsahuje plně kvalifikovaný název položky.

## <a name="global-suppression-file"></a>Globální soubor potlačení
 Globální soubor potlačení uchovává potlačení, která jsou buď potlačená, nebo potlačení, která neurčují cíl. Například potlačení pro porušení úrovně sestavení se ukládají do tohoto souboru. Kromě toho jsou v tomto souboru uložena některá potlačení ASP.NET, protože nastavení na úrovni projektu nejsou k dispozici pro kód za formulářem. Globální potlačení je vytvořeno a přidáno do projektu při prvním výběru možnosti **v souboru potlačení projektu** v příkazu pro **potlačení zpráv** v okně Seznam chyb. Další informace naleznete v tématu [How to: potlačení upozornění pomocí položky nabídky](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md).

## <a name="see-also"></a>Viz také
 <xref:System.Diagnostics.CodeAnalysis>
