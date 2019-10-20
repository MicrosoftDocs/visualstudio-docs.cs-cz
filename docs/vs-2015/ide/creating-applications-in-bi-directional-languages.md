---
title: Vytváření aplikací v obousměrných jazycích | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3b3d8649484178a537ed4af7bdde044a29893275
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72619265"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Vytváření aplikací v obousměrných jazycích
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí sady Visual Studio můžete vytvářet aplikace, které správně zobrazují text v jazycích psaných zprava doleva, včetně arabštiny a hebrejštiny. U některých funkcí můžete jednoduše nastavit vlastnosti. V jiných případech je nutné implementovat funkce v kódu.

> [!NOTE]
> Aby bylo možné zadávat a zobrazovat obousměrné jazyky, musíte pracovat s verzí systému Windows, která je nakonfigurovaná s odpovídajícím jazykem. Může to být buď Anglická verze systému Windows s nainstalovanou příslušnou jazykovou sadou, nebo odpovídající lokalizovaná verze systému Windows.

## <a name="types-of-application-that-support-bi-directional-languages"></a>Typy aplikací podporujících obousměrné jazyky

1. Aplikace systému Windows. Můžete vytvářet plně obousměrné aplikace, které zahrnují podporu obousměrného textu, pořadí čtení zprava doleva a zrcadlení (převrácení rozložení oken, nabídek, dialogových oken atd.). S výjimkou zrcadlení jsou tyto funkce k dispozici ve výchozím nastavení nebo jako nastavení vlastností. Zrcadlení je v podstatě podporováno pro některé funkce, jako jsou například okna se zprávami. V jiných případech však musíte implementovat zrcadlení v kódu. Další informace najdete v tématu [Podpora obousměrného škálování pro aplikace model Windows Forms](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2).

2. Webové aplikace. Webové služby podporují a přijímají posílání textu UTF-8 a Unicode, takže jsou vhodné pro aplikace, které se týkají obousměrných jazyků. Webové klientské aplikace spoléhají na své uživatelské rozhraní v prohlížečích, takže stupeň obousměrné podpory ve webové aplikaci závisí na tom, jak dobře podporuje prohlížeč uživatelů tyto funkce v obousměrném směru. V aplikaci Visual Studio můžete vytvářet aplikace s podporou arabského nebo hebrejského textu, pořadí čtení zprava doleva, kódování souborů a nastavení místní kultury. Další informace najdete v tématu [Obousměrná podpora pro webové aplikace ASP.NET](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03).

3. Konzolové aplikace. Konzolové aplikace neobsahují podporu textu pro obousměrné jazyky. Jedná se o postup, jak systém Windows funguje s aplikacemi konzoly.

## <a name="visual-studio-features-that-are-fully-supported"></a>Funkce sady Visual Studio, které jsou plně podporovány
 V době návrhu v aplikaci Visual Studio můžete použít obousměrné jazyky v těchto způsobech:

- **Zadávání textu** Sada Visual Studio podporuje kódování Unicode, takže pokud je systém nastavený na odpovídající národní prostředí a vstupní jazyk, můžete zadat text v arabštině nebo hebrejštině. (Podpora arabštiny zahrnuje kašidy a diakritická znaménka.)

- **Názvy objektů** Obousměrné jazyky můžete použít k přiřazení názvů k řešením, projektům, souborům, složkám a tak dále. V kódu můžete použít obousměrné jazyky pro názvy proměnných, tříd, objektů, atributů, metadat a dalších prvků.

- **Kódování souboru** Soubory můžete ukládat a otevírat pomocí kódování pro konkrétní jazyk nebo Unicode. Další informace najdete v tématu [Postupy: ukládání a otevírání souborů s kódováním](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-or-no-support"></a>Funkce s omezením nebo bez podpory
 Jiné funkce, které jsou společné pro obousměrné jazykové aplikace, nejsou v aplikaci Visual Studio plně podporované nebo v některých případech vůbec ne. Zde jsou některé z nich:

- **Pořadí čtení zprava doleva** Ve výchozím nastavení používají ovládací prvky pro zadávání textu v aplikaci Visual Studio směr čtení zleva doprava. Ve většině případů můžete použít standardní gesta Windows k přepínání pořadí čtení. Například můžete stisknout kombinaci kláves CTRL + SHIFT + Shift a přepnout okno Vlastnosti tak, aby podporovala pořadí čtení zprava doleva pro hodnoty vlastností.

  Nicméně směr čtení zprava doleva není podporován všude v aplikaci Visual Studio. Mezi výjimky patří:

  - Zaškrtávací políčka, rozevírací seznamy a další ovládací prvky v dialogových oknech sady Visual Studio vždy používají pořadí čtení zleva doprava.

  - Editor kódu (a textový editor) nepodporuje pořadí čtení zprava doleva. Můžete zadat text v obousměrném jazyce, ale pořadí čtení je vždy zleva doprava.

## <a name="naming-things-using-arabic-or-hebrew-text"></a>Pojmenování pomocí arabského nebo hebrejského textu
 Pomocí arabského nebo hebrejského textu můžete přiřadit názvy ke složkám, proměnným nebo jiným objektům. Při práci s Arabština můžete použít všechny arabské znaky včetně kašidy a diakritiky.

 Následující prvky mohou být pojmenovány pomocí arabštiny nebo hebrejštiny a budou správně zpracovány v aplikaci Visual Studio:

- Názvy řešení, projektů a souborů, včetně všech složek, které jsou obsaženy v cestě projektu. Průzkumník řešení budou správně zobrazovat názvy řešení a prvků.

- Obsah souboru. Soubory můžete otevřít nebo uložit s kódováním Unicode nebo pomocí vybrané znakové stránky.

    > [!NOTE]
    > Editor kódu je zvláštní případ. Podrobnosti najdete níže.

- Datové prvky. **Průzkumník serveru** zobrazí tyto prvky správně a umožní vám jejich úpravy.

- Prvky zkopírované do schránky systému Windows.

- Atributy a metadata.

- Hodnoty vlastností. V okno Vlastnosti můžete použít arabský nebo hebrejský text. Okno umožňuje přepínat mezi směry čtení zprava doleva a zleva doprava pomocí standardních klávesových úhozů systému Windows (CTRL + RightShift pro zprava doleva a kombinací kláves CTRL + LeftShift pro zleva doprava).

- Kód a literální text. V editoru kódu (což je také textový editor) můžete použít arabštinu nebo hebrejštinu k pojmenování tříd, funkcí, proměnných, vlastností, řetězcových literálů, atributů a tak dále. Editor však nepodporuje pořadí čtení zprava doleva; text vždy začíná levým okrajem.

    > [!TIP]
    > Doporučuje se umístit řetězcové literály do souborů prostředků namísto hardwarového kódování do programů. Další informace naleznete v tématu [Návod: lokalizace model Windows Forms](https://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5).

    > [!NOTE]
    > Musíte být konzistentní v tom, jak odkazujete na objekty s názvem v těchto jazycích. Pokud například použijete kašidy při pojmenování arabské proměnné, při odkazování na tuto proměnnou je vždy nutné použít kašidy, jinak dojde k chybám.

- Komentáře ke kódu. Můžete vytvářet komentáře v arabštině nebo hebrejštině. Tyto jazyky můžete použít také v nástroji Tvůrce poznámek.

## <a name="see-also"></a>Viz také
 Obousměrná [Podpora pro model Windows Forms aplikace](https://msdn.microsoft.com/library/7b622fa4-f390-4e4d-b624-83a1917cccf2) [Obousměrná podpora pro webové aplikace ASP.NET](https://msdn.microsoft.com/library/5576f9b1-9b86-41ef-8354-092d366bcd03) , které [globalizací](../ide/globalizing-applications.md) aplikace [lokalizace aplikací](../ide/localizing-applications.md)
