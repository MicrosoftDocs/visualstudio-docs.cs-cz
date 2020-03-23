---
title: Podpora arabštiny a hebrejštiny
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bccfccb77c5a80fd2630680564f88f08d7ca5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591993"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Podpora obousměrných jazyků v sadě Visual Studio

Visual Studio může správně zobrazit arabský a hebrejský text a umožňuje zadat obousměrný text pro názvy a hodnoty objektů.

> [!NOTE]
> Chcete-li zadávat a zobrazovat obousměrné jazyky, musíte pracovat s verzí systému Windows, která je nakonfigurována s příslušným jazykem. Může se jedná buď o anglickou verzi systému Windows s nainstalovanou příslušnou jazykovou sadou, nebo o vhodně lokalizovanou verzi systému Windows.

## <a name="fully-supported-features"></a>Plně podporované funkce

V době návrhu v sadě Visual Studio můžete používat obousměrné jazyky při zadávání textu, pojmenovávání objektů a při ukládání a otevírání souborů.

### <a name="text-entry"></a>Zadání textu

Visual Studio podporuje Unicode, takže pokud je váš systém nastaven na příslušné národní prostředí a vstupní jazyk, můžete zadat text v arabštině nebo hebrejštině. (Arabská podpora zahrnuje Kašidu a diakritiku.)

### <a name="arabic-or-hebrew-object-names"></a>Názvy arabských nebo hebrejských objektů

Obousměrné jazyky můžete použít k přiřazení názvů řešením, projektům, souborům, složkám a tak dále. V kódu můžete použít obousměrné jazyky pro názvy proměnných, tříd, objektu, atributů, metadat a dalších prvků. Při práci s arabštinou můžete použít libovolné arabské znaky včetně Kašidy a diakritiky.

Následující prvky mohou být pojmenovány pomocí arabštiny nebo hebrejštiny a jsou správně zpracovány Visual Studio:

- Názvy řešení, projektu a souborů, včetně všech složek, které zahrnete do cesty projektu.

   **Průzkumník řešení** zobrazí názvy řešení a prvků správně.

- Obsah souboru.

   Soubory můžete otevírat nebo ukládat pomocí kódování Unicode nebo s vybranou znakovou stránkou.

- Datové prvky.

   **Průzkumník serveru** zobrazí tyto prvky správně a můžete je upravit.

- Prvky zkopírované do schránky systému Windows.

- Atributy a metadata.

- Hodnoty vlastností.

   V okně **Vlastnosti** můžete použít arabský nebo hebrejský text. Okno umožňuje přepínat mezi pořadím čtení zprava doleva a zleva doprava pomocí standardních úhozů systému Windows **(Ctrl**+**RightShift** pro right-to-left a **Ctrl**+**LeftShift** pro zleva doprava).

- Kód a doslovný text.

   V editoru kódu můžete použít arabštinu nebo hebrejštinu k pojmenování tříd, funkcí, proměnných, vlastností, řetězcových literál, atributů a tak dále. Editor však nepodporuje pořadí čtení zprava doleva; text vždy začíná na levém okraji.

   > [!TIP]
   > Měli byste umístit řetězcové literály do souborů prostředků namísto jejich pevného kódování do programů. Další informace naleznete [v tématu Prostředky v aplikacích klasické pracovní plochy (.NET Framework)](/dotnet/framework/resources/index).

   > [!NOTE]
   > Musíte být konzistentní v tom, jak odkazujete na objekty pojmenované v arabštině a hebrejštině. Pokud například používáte Kašidu při pojmenování arabské proměnné, musíte vždy použít Kašidu, když odkazujete na tuto proměnnou, nebo dojde k chybám.

- Komentáře kódu. Komentáře můžete vytvářet v arabštině nebo hebrejštině. Tyto jazyky můžete také použít v nástroji pro tvorbu poznámek.

### <a name="file-encoding"></a>Kódování souborů

Soubory můžete ukládat a otevírat pomocí kódování specifického pro jazyk nebo kódování Unicode. Další informace naleznete v [tématu Postup: Ukládání a otevírání souborů pomocí kódování](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="right-to-left-reading-order"></a>Pořadí čtení zprava doleva

Visual Studio má omezenou podporu pro pořadí čtení zprava doleva. Ve výchozím nastavení ovládací prvky zadávání textu v sadě Visual Studio používají pořadí čtení zleva doprava. Ve většině případů můžete k přepnutí pořadí čtení použít standardní gesta systému Windows. Můžete například stisknutím **klávesy Ctrl**+**RightShift** přepnout okno **Vlastnosti** pro podporu pořadí čtení zprava doleva pro hodnoty vlastností.

Pořadí čtení zprava doleva není v aplikaci Visual Studio podporováno na následujících místech:

- Zaškrtávací políčka, rozevírací seznamy a další ovládací prvky v dialogových oknech sady Visual Studio vždy používají pořadí čtení zleva doprava.

- Editor kódu (a textový editor) nepodporuje pořadí čtení zprava doleva. Text můžete zadávat obousměrným jazykem, ale pořadí čtení je vždy zleva doprava.

## <a name="see-also"></a>Viz také

- [Vývoj globalizovaných a lokalizovaných aplikací](globalizing-and-localizing-applications.md)
