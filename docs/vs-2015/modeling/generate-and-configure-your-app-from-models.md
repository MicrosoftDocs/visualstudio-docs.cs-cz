---
title: Generování a konfigurace aplikace z modelů | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 4dc8f572-a09e-4d19-a92d-f1df383e728b
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2ea9e28c55b608235d49096e4ef99cd30081eda0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666167"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generování a konfigurace aplikace z modelů
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete vygenerovat nebo nakonfigurovat části aplikace z modelu. Model může být v UML nebo DSL.

 Model představuje více požadavků přímo než kód. Odvozením chování aplikace přímo z modelu můžete reagovat na změněné požadavky mnohem rychleji a spolehlivější než prostřednictvím aktualizace kódu. I když je k nastavení odvození potřeba některá počáteční práce, tato investice se vrátí, pokud očekáváte změny v požadavcích, nebo pokud máte v plánu provést několik variant produktu.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generování kódu vaší aplikace z modelu
 Nejjednodušší způsob, jak vygenerovat kód, je použití textových šablon. Kód můžete vygenerovat ve stejném [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] řešení, ve kterém model udržujete. Další informace naleznete v tématu:

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md)

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)

  Tato metoda se dá snadno použít přírůstkově. Začněte s aplikací, která funguje jenom pro konkrétní případ, a vyberte několik částí, které se mají od modelu lišit. Přejmenujte zdrojové soubory těchto částí tak, aby se staly soubory textových šablon (. TT). V tomto okamžiku budou zdrojové soubory. cs automaticky vygenerovány ze souborů šablony, takže aplikace bude fungovat stejně jako dříve.

  Potom můžete provést jednu část kódu a nahradit ji výrazem textové šablony, který čte model a generuje tuto část zdrojového souboru. Nejméně jedna hodnota modelu by měla vygenerovat původní zdroj, takže znovu můžete spustit aplikaci a bude fungovat stejně jako dříve. Po otestování různých hodnot modelu můžete přejít na a vložit výrazy šablony do jiné části kódu.

  Tato přírůstková metoda znamená, že generování kódu je obvykle přístup s nízkou rizikovostí. Výsledné aplikace obvykle vyplývají z toho skoro i ručně psaná verze.

  Pokud však začnete s existující aplikací, může dojít k tomu, že k oddělení různých chování, které se řídí modelem, je nutné provést mnoho refaktoringu, aby bylo možné je nezávisle měnit. Doporučujeme, abyste vyhodnotili tento aspekt aplikace při odhadování nákladů na projekt.

## <a name="configuring-your-application-from-a-model"></a>Konfigurace aplikace z modelu
 Chcete-li změnit chování aplikace za běhu, nemůžete použít generování kódu, který generuje zdrojový kód před zkompilováním aplikace. Místo toho můžete aplikaci navrhnout tak, aby si přečetla model UML nebo DSL a aby se odpovídajícím způsobem lišilo jeho chování. Další informace naleznete v tématu:

- [Čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md)

- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Tato metoda se dá použít taky přírůstkově, ale na začátku je víc práce. Je nutné napsat kód, který načte model, a nastavit rozhraní, které umožní přístup k jeho hodnotám proměnným části. Vytváření obecných částí proměnných je dražší než generování kódu.

  Obecná aplikace obvykle provádí méně, než je jejich konkrétní protějšky. Pokud je rozhodující výkon, váš plán projektu by měl zahrnovat posouzení tohoto rizika.

## <a name="developing-a-derived-application"></a>Vývoj odvozené aplikace
 Můžete najít následující obecné pokyny, které jsou užitečné.

- **Spusťte konkrétní a pak generalizujte.** Nejdřív napište konkrétní verzi aplikace. Tato verze by měla fungovat v jedné sadě podmínek. Pokud jste přesvědčeni, že funguje správně, můžete některé z nich odvodit z modelu. Postupně rozšíříte odvozené části.

     Například Navrhněte web, který má konkrétní sadu webových stránek před návrhem webové aplikace, která obsahuje stránky definované v modelu.

- **Modelujte aspekty variant.** Identifikujte aspekty, které se budou lišit, buď mezi jedním nasazením a další, nebo v průběhu času podle změny požadavků. Toto jsou aspekty, které by měly být odvozeny z modelu.

     Například pokud se sada webových stránek a propojení mezi nimi změní, ale styl a formát stránek jsou vždy stejné, pak model musí popsat odkazy, ale nemusí popsán formát stránek.

- **Nezávislé obavy.** Pokud se aspekty proměnných dají rozdělit na nezávislé oblasti, použijte pro každou oblast samostatné modely. Pomocí ModelBus můžete definovat operace, které ovlivňují oba modely, a omezení mezi nimi.

     Například použijte jeden model k definování navigace mezi webovými stránkami a jiným modelem pro definování rozložení stránek. Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

- **Vymodelujte požadavek, ne řešení.** Navrhněte DSL nebo Přizpůsobte UML, aby bylo popsáno požadavky uživatele. Naopak nenavrhovat zápis podle proměnných aspektů implementace.

     Například webový navigační model musí představovat webové stránky a hypertextové odkazy. Webový navigační model by neměl představovat fragmenty HTML nebo tříd ve vaší aplikaci.

- **Generovat nebo interpretovat?** Pokud se požadavky na konkrétní nasazení zřídka mění, vygenerujte programový kód z modelu. Pokud se požadavky často mění nebo můžou existovat ve více než jedné variantě ve stejném nasazení, napište aplikaci tak, aby mohla číst a interpretovat model.

     Pokud například použijete váš model webu k vývoji řady různých a samostatně instalovaných webů, pak byste měli z modelu vygenerovat kód lokality. Ale použijete svůj model k řízení lokality, která se každý den mění, pak je lepší napsat webový server, který čte model a prezentuje web odpovídajícím způsobem.

- **UML nebo DSL?** Zvažte vytvoření zápisu modelování pomocí stereotypů pro rozšiřování UML. Definujte DSL, pokud není k dispozici žádný diagram UML, který by odpovídal účelu. Ale Vyhněte se narušení standardní sémantiky UML.

     Například diagram tříd UML je kolekce polí a šipek. v tomto Notation můžete v teoreticky definovat cokoli. Nedoporučuje se ale používat diagram tříd s výjimkou případů, kdy jste ve skutečnosti popisují sadu typů. Například můžete přizpůsobovat diagramy tříd pro popis různých typů webových stránek.

## <a name="see-also"></a>Viz také
 [Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md) [čtení modelu UML v kódu programu](../modeling/read-a-uml-model-in-program-code.md) [generování kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md) [Postupy: otevření modelu ze souboru ve](../modeling/how-to-open-a-model-from-file-in-program-code.md) [generování kódu při návrhu kódu programu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
