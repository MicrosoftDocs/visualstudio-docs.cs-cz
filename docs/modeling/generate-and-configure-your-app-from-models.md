---
title: Generování a konfigurace aplikace z modelů
description: Zjistěte, co model představuje a jak můžete generovat nebo konfigurovat části aplikace z modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68339159ed9926490f22a82cd30ce69f45ab6a30
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388864"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generování a konfigurace aplikace z modelů
Části aplikace můžete vygenerovat nebo nakonfigurovat z modelu.

 Model představuje požadavky přímo než kód. Odvozením chování aplikace přímo z modelu můžete reagovat na změněné požadavky mnohem rychleji a spolehlivěji než aktualizací kódu. I když je k nastavení odvozování nutné provést určité počáteční práce, tato investice se vrátí, pokud očekáváte změny v požadavcích nebo pokud plánujete vytvořit několik variant produktu.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generování kódu aplikace z modelu
 Nejjednodušší způsob, jak vygenerovat kód, je pomocí textových šablon. Kód můžete vygenerovat ve stejném Visual Studio, ve kterém model uchováte. Další informace naleznete v tématu:

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)

  Tato metoda se snadno používá přírůstkově. Začněte s aplikací, která funguje jenom pro konkrétní případ, a zvolte několik částí, které chcete od modelu lišit. Přejmenujte zdrojové soubory těchto částí tak, aby se z nich staly textové soubory šablony (.tt). V tomto okamžiku se ze souborů šablony automaticky vygenerují zdrojové soubory .cs, takže aplikace bude fungovat stejně jako předtím.

  Pak můžete vzít jednu část kódu a nahradit ji výrazem textové šablony, který přečte model a vygeneruje ji ve zdrojovém souboru. Alespoň jedna hodnota modelu by měla vygenerovat původní zdroj, abyste aplikaci mohli znovu spustit a fungovala stejně jako předtím. Po otestování různých hodnot modelu můžete přejít k vložení výrazů šablony do jiné části kódu.

  Tato přírůstková metoda znamená, že generování kódu je obvykle přístup s nízkým rizikem. Výsledné aplikace obvykle provádějí téměř stejně jako ručně psané verze.

  Pokud ale začnete s existující aplikací, můžete zjistit, že k oddělení různých chování, která se řídí modelem, je potřeba hodně refaktoringu, aby bylo možné je nezávisle měnit. Doporučujeme posoudit tento aspekt aplikace při odhadu nákladů na projekt.

## <a name="configuring-your-application-from-a-model"></a>Konfigurace aplikace z modelu
 Pokud chcete měnit chování aplikace za běhu, nemůžete použít generování kódu, které generuje zdrojový kód před kompilaci aplikace. Místo toho můžete aplikaci navrhnout tak, aby četla model, a odpovídajícím způsobem odlišit její chování. Další informace naleznete v tématu:

- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Tuto metodu lze také použít přírůstkově, ale na začátku je více práce. Musíte napsat kód, který bude číst model, a nastavit rozhraní, které umožní přístup k jeho hodnotám pro části proměnných. Obecné nastavení proměnných částí je dražší než generování kódu.

  Obecná aplikace obvykle provádí méně dobře než její konkrétní protějšky. Pokud je výkon zásadní, měl by váš plán projektu zahrnovat posouzení tohoto rizika.

## <a name="developing-a-derived-application"></a>Vývoj odvozené aplikace
 Následující obecné pokyny můžou být užitečné.

- **Začněte konkrétně a pak zobecnit.** Nejprve napište konkrétní verzi aplikace. Tato verze by měla fungovat v jedné sadě podmínek. Pokud jste spokojeni s tím, že funguje správně, můžete některé z těchto vlastností odvodit z modelu. Rozšiřte odvozené části postupně.

     Můžete například navrhnout web, který má konkrétní sadu webových stránek, než navrhovat webovou aplikaci, která bude prezentovat stránky definované v modelu.

- **Modelovat variantní aspekty.** Identifikujte aspekty, které se budou lišit, ať už mezi jedním a druhým, nebo v průběhu času podle toho, jak se požadavky mění. Jedná se o aspekty, které by měly být odvozeny z modelu.

     Pokud se například změní sada webových stránek a propojení mezi nimi, ale styl a formát stránek jsou vždy stejné, měl by model popisovat odkazy, ale nemusí popisovat formát stránek.

- **Samostatné obavy.** Pokud lze aspekty proměnných rozdělit do nezávislých oblastí, použijte pro každou oblast samostatné modely. Pomocí modelbusu můžete definovat operace, které ovlivňují oba modely, a omezení mezi nimi.

     Pomocí jednoho modelu můžete například definovat navigaci mezi webovými stránkami a jiným modelem pro definování rozložení stránek.

- **Modeluje požadavek, nikoli řešení.** Navrhovat model tak, aby popisuje požadavky uživatelů. Naopak nenavrhovat notaci podle proměnných aspektů implementace.

     Model webové navigace by například měl představovat webové stránky a hypertextové odkazy mezi nimi. Model webové navigace by neměl představovat fragmenty kódu HTML nebo tříd ve vaší aplikaci.

- **Generovat nebo interpretovat?** Pokud se požadavky na konkrétní nasazení zřídka změní, vygenerování programového kódu z modelu. Pokud se požadavky můžou často měnit nebo mohou existovat ve více variantách ve stejném nasazení, napište aplikaci, aby mohla číst a interpretovat model.

     Pokud například použijete model webu k vývoji řady různých a samostatně nainstalovaných webů, měli byste z modelu vygenerovat kód webu. Model ale použijete k řízení webu, který se každý den mění, a pak je lepší napsat webový server, který čte model a odpovídajícím způsobem prezentuje web.

- **UML nebo DSL?** Zvažte vytvoření notace modelování pomocí stereotypů k rozšíření UML. Definujte DSL, pokud neexistuje žádný diagram UML, který by tomuto účelu odpovídá. Vyhněte se ale porušení standardní sémantiky UML.

     Například diagram tříd UML je kolekce polí a šipek. Pomocí tohoto notace můžete teoreticky definovat cokoli. Nedoporučujeme ale používat diagram tříd s výjimkou případů, kdy ve skutečnosti popisujete sadu typů. Diagramy tříd můžete například přizpůsobit pro popis různých typů webových stránek.

## <a name="see-also"></a>Viz také

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
