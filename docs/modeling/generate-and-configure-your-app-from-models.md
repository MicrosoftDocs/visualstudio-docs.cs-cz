---
title: Generování a konfigurace aplikace z modelů
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 78dc0907fa717f61b6cf883994a3ac2fd6072ba1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49872795"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generování a konfigurace aplikace z modelů
Můžete vytvořit nebo nakonfigurovat částí aplikace z modelu.

 Model představuje požadavky přímo do kódu. Odvozením chování aplikace přímo z modelu můžete reagovat na změny požadavky mnohem rychleji a spolehlivěji než podle aktualizací kódu. I když některé počáteční pracovní je nutné nastavit odvození, tyto investice je vrácena, pokud očekáváte, že změny v požadavcích, nebo pokud plánujete udělat několik variant produktu.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generování kódu vaší aplikace z modelu
 Nejjednodušší způsob, jak generovat kód je pomocí textových šablon. Generování kódu ve stejném řešení sady Visual Studio, ve kterém můžete zachovat modelu. Další informace naleznete v tématu:

- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)

  Tato metoda je snadno použitelná postupně. Začněte s aplikaci, která se dá použít jenom pro konkrétní případ a zvolit několik částí, které chcete z modelu se liší. Přejmenujte zdrojové soubory z těchto částí, takže budou soubory textových šablon (.tt). V tomto okamžiku zdrojové soubory .cs automaticky se vygeneruje z soubory šablon, aplikace bude fungovat jako předtím.

  Potom může trvat jednu část kódu a nahraďte výraz šablony textu, který čte model a generuje část zdrojového souboru. Nejméně jedna hodnota modelu by měl generovat původního zdroje, takže můžete znovu spustit aplikaci a bude fungovat jako předtím. Po otestování hodnoty jiný model, můžete přesunout vložit výrazy šablony do jiné části kódu.

  Tato metoda přírůstkové znamená, že generování kódu je obvykle přístup s nízkým rizikem. Výsledná aplikace obvykle provádět téměř stejně ručně psanou verze.

  Ale pokud byste začali s existující aplikaci, můžete zjistit, že velké množství refaktoring, je potřeba oddělit různé chování, které se řídí modelem tak, aby může být nejrůznější nezávisle na sobě. Doporučujeme posoudit tento aspekt aplikace při odhadnout náklady na váš projekt.

## <a name="configuring-your-application-from-a-model"></a>Konfigurace vaší aplikace z modelu
 Pokud chcete definovat různé chování vaší aplikace v době běhu, nemůžete použít generování kódu, který generuje zdrojový kód, předtím, než bude uložena zkompilovaná aplikace. Místo toho můžete navrhnout vaše aplikace se má načíst model a odpovídajícím způsobem měnit své chování. Další informace naleznete v tématu:

- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Tuto metodu lze použít také postupně, ale existuje více práce na začátku. Budete muset napsat kód, který bude načíst model a nastavit rozhraní, které umožňuje její hodnoty dostupná pro proměnné částí. Vytváření proměnných části Obecné je nákladnější než generování kódu.

  Obecná aplikace obvykle provádí méně dobře než její konkrétní protějšky. Pokud je výkon velmi důležitý, by měl obsahovat svůj plán projektu posouzení rizika.

## <a name="developing-a-derived-application"></a>Vývoj odvozené aplikace
 Můžou být užitečné následující obecné pokyny.

-   **Spustit konkrétní a generalizace.** Nejprve napište konkrétní verzi vaší aplikace. Tato verze by měla fungovat v jedné sadě podmínek. Jakmile budete spokojeni se pracuje správně, můžete provést některé z jeho odvození z modelu. Rozšiřte odvozené části postupně.

     Třeba návrh webu, který má specifickou sadu webových stránek, než bude možné navrhnout webové aplikace, která představuje stránek, které jsou definovány v modelu.

-   **Model variant aspekty.** Identifikujte aspekty, které se liší, buď mezi jedno nasazení a další, nebo v čase jako požadavky změnit. Jedná se o jejich aspekty, které by měla být odvozena z modelu.

     Pokud sadu webových stránek a odkazů mezi jejich změny ale styl a formátování stránek je vždy stejný, a měl by popisovat odkazy modelu, ale nemá k popisu formátu stránky.

-   **Zvláštní aspekty.** Pokud proměnné aspekty je možné rozdělit do nezávislých oblasti, použití samostatných modelů pro každou oblast. Pomocí ModelBus, můžete definovat operace, které ovlivňují modely a omezení mezi nimi.

     Například definovat navigaci mezi stránkami webové a jiný model, pokud chcete definovat rozložení stránek pomocí jeden model.

-   **Model požadavku, nikoli řešení.** Návrh modelem tak, aby popisuje požadavky uživatelů. Naopak nenavrhujte zápis podle proměnné aspekty implementace.

     Například model navigace webové by měla představovat webových stránek a hypertextových odkazů mezi nimi. Model navigace webové by neměla představovat fragmenty kódu HTML nebo tříd v aplikaci.

-   **Generovat nebo interpretace?** Pokud požadavky pro konkrétní nasazení se jen zřídka mění, generování programového kódu z modelu. Pokud požadavky můžou často měnit, nebo může existovat vedle sebe ve více než jednu hodnotu typu variant v jednom nasazení, zapište aplikaci tak, aby může číst a interpretovat modelu.

     Například pokud používáte model webu pro vývoj řadu různých a samostatně instalovaný webových stránek, pak by měl vygenerujete kód lokality z modelu. Ale ho použijete model k řízení lokality, která se každý den mění, je lepší pro zápis webový server, který čte model a odpovídajícím způsobem zobrazí webu.

-   **UML nebo DSL?** Zvažte vytvoření zápis modelování s využitím Stereotypy pro rozšíření UML. Definice DSL, pokud neexistuje žádný diagram UML, která odpovídá účel. Ale vyhnuli narušení funkčnosti standardní sémantiku UML.

     Diagram tříd UML je například kolekce polí a šipky; v tomto zápisu můžete teoreticky definovat cokoli. Ale nedoporučujeme používat s výjimkou případů, ve kterém jsou ve skutečnosti popisující sadu typů diagramu tříd. Může například přizpůsobení diagramů tříd k popisu různých typů webových stránek.

## <a name="see-also"></a>Viz také

- [Vytváření kódu z jazyka specifického pro doménu](../modeling/generating-code-from-a-domain-specific-language.md)
- [Postupy: Otevření modelu ze souboru v kódu programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Vytvoření kódu v době návrhu pomocí textových šablon T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)