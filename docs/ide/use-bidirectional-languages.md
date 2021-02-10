---
title: Podpora pro arabštinu a hebrejštinu
description: Naučte se, jak zobrazit arabskou a hebrejskou text a zadat obousměrný text pro názvy a hodnoty objektů.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a16aa4d445878ac8d357fa551e46552a1465bfe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971346"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Podpora obousměrných jazyků v aplikaci Visual Studio

Visual Studio může zobrazit arabský a hebrejský text správně a umožňuje zadat obousměrný text pro názvy a hodnoty objektů.

> [!NOTE]
> Aby bylo možné zadávat a zobrazovat obousměrné jazyky, musíte pracovat s verzí systému Windows, která je nakonfigurovaná s odpovídajícím jazykem. Může to být buď Anglická verze systému Windows s nainstalovanou příslušnou jazykovou sadou, nebo odpovídající lokalizovaná verze systému Windows.

## <a name="fully-supported-features"></a>Plně podporované funkce

V době návrhu v aplikaci Visual Studio můžete používat obousměrné jazyky při zadávání textu, pojmenovávání objektů a při ukládání a otevírání souborů.

### <a name="text-entry"></a>Zadání textu

Sada Visual Studio podporuje kódování Unicode, takže pokud je systém nastavený na odpovídající národní prostředí a vstupní jazyk, můžete zadat text v arabštině nebo hebrejštině. (Podpora arabštiny zahrnuje kašidy a diakritická znaménka.)

### <a name="arabic-or-hebrew-object-names"></a>Arabské nebo hebrejské názvy objektů

Obousměrné jazyky můžete použít k přiřazení názvů k řešením, projektům, souborům, složkám a tak dále. V kódu můžete použít obousměrné jazyky pro názvy proměnných, tříd, objektů, atributů, metadat a dalších prvků. Při práci s Arabština můžete použít všechny arabské znaky včetně kašidy a diakritiky.

Následující prvky mohou být pojmenovány pomocí arabštiny nebo hebrejštiny a jsou zpracovány správně pomocí sady Visual Studio:

- Názvy řešení, projektů a souborů, včetně všech složek, které jsou obsaženy v cestě projektu.

   **Průzkumník řešení** zobrazuje správně názvy řešení a prvků.

- Obsah souboru.

   Soubory můžete otevřít nebo uložit s kódováním Unicode nebo pomocí vybrané znakové stránky.

- Datové prvky.

   **Průzkumník serveru** zobrazí tyto prvky správně a můžete je upravit.

- Prvky zkopírované do schránky systému Windows.

- Atributy a metadata.

- Hodnoty vlastností.

   V okně **vlastnosti** můžete použít arabský nebo Hebrejská text. Okno umožňuje přepínat mezi směry čtení zprava doleva a zleva doprava pomocí standardních klávesových úhozů systému Windows (**CTRL** + **RightShift** for zprava doleva a **kombinací kláves CTRL** + **LeftShift** zleva doprava).

- Kód a literální text.

   V editoru kódu můžete použít arabštinu nebo hebrejštinu k pojmenování tříd, funkcí, proměnných, vlastností, řetězcových literálů, atributů a tak dále. Editor však nepodporuje pořadí čtení zprava doleva; text vždy začíná levým okrajem.

   > [!TIP]
   > Řetězcové literály byste měli umístit do souborů prostředků namísto jejich hardwarového kódování do programů. Další informace najdete v tématu [prostředky v aplikacích klasické pracovní plochy (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Musíte být konzistentní v tom, jak odkazujete na objekty s názvem v arabštině a hebrejštině. Pokud například použijete kašidy při pojmenování arabské proměnné, je nutné vždy použít kašidy při odkazování na tuto proměnnou nebo chyby.

- Komentáře ke kódu. Můžete vytvářet komentáře v arabštině nebo hebrejštině. Tyto jazyky můžete použít také v nástroji Tvůrce poznámek.

### <a name="file-encoding"></a>Kódování souboru

Soubory můžete ukládat a otevírat pomocí kódování pro konkrétní jazyk nebo Unicode. Další informace najdete v tématu [Postupy: ukládání a otevírání souborů s kódováním](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Pořadí čtení zprava doleva

Visual Studio má omezené podpory pro pořadí čtení zprava doleva. Ve výchozím nastavení používají ovládací prvky pro zadávání textu v aplikaci Visual Studio směr čtení zleva doprava. Ve většině případů můžete použít standardní gesta Windows k přepínání pořadí čtení. Můžete například stisknout **kombinaci kláves CTRL** + **RightShift** a přepnout okno **vlastnosti** tak, aby se pro hodnoty vlastností podporovalo pořadí čtení zprava doleva.

Směr čtení zprava doleva není podporován na následujících místech v aplikaci Visual Studio:

- Zaškrtávací políčka, rozevírací seznamy a další ovládací prvky v dialogových oknech sady Visual Studio vždy používají pořadí čtení zleva doprava.

- Editor kódu (a textový editor) nepodporuje pořadí čtení zprava doleva. Text můžete zadat v obousměrném jazyce, ale pořadí čtení je vždy zleva doprava.

## <a name="see-also"></a>Viz také

- [Vývoj globálních a lokalizovaných aplikací](globalizing-and-localizing-applications.md)
