---
title: Vytváření aplikací v obousměrných jazycích
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9f93dea099d9223347c727f3e7a838fcb78d3742
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863631"
---
# <a name="creating-applications-in-bi-directional-languages"></a>Vytváření aplikací v obousměrných jazycích

Visual Studio můžete vytvářet aplikace pro správné zobrazení textu v jazycích napsané-doleva, včetně arabština a hebrejština. Pro některé funkce stačí nastavit vlastnosti. V ostatních případech je nutné implementovat v kódu funkce.

> [!NOTE]
> Pokud chcete zadat a zobrazit obousměrných jazycích, musíte pracovat s verzí Windows, který je nakonfigurován příslušný jazyk. To může být buď anglickou verzi systému Windows s odpovídající jazyková sada nainstalovaná nebo správně lokalizovanou verzi Windows.

## <a name="types-of-application-that-support-bi-directional-languages"></a>Typy aplikací, které podporují obousměrných jazycích

-  Aplikace Windows. Můžete vytvořit plně obousměrnou aplikace, které zahrnují podporu pro obousměrný text zprava doleva pořadí čtení a zrcadlení (reverzní rozložení windows, nabídek, dialogová okna a tak dále). S výjimkou zrcadlení, tyto funkce jsou dostupné ve výchozím nastavení nebo nastavení vlastností. Zrcadlení se podporuje ze své podstaty pro některé funkce, jako jsou okna se zprávou. Ale v ostatních případech je nutné implementovat zrcadlení v kódu. Další informace najdete v tématu [obousměrná podpora pro aplikace Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

-  Webové aplikace. Webové služby, podpora a přijímají odesílání UTF-8 a Unicode textu, díky kterým jsou vhodné pro aplikace zahrnující obousměrných jazycích. Webové klientské aplikace využívají prohlížeče pro uživatelské rozhraní, tedy závisí na tom, jak dobře webového prohlížeče podporuje tyto funkce obousměrné stupeň obousměrná podpora ve webové aplikaci. V sadě Visual Studio můžete vytvářet aplikace s podporou arabský nebo hebrejský text, pořadí čtení zprava doleva, kódování souborů a nastavení místní jazykové verze. Další informace najdete v tématu [obousměrná podpora pro webové aplikace ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

-  Konzolová aplikace. Konzolové aplikace nezahrnují text podpora obousměrných jazycích. Toto je v důsledku toho, jak funguje Windows pomocí konzolové aplikace.

## <a name="visual-studio-features-that-are-fully-supported"></a>Funkce sady Visual Studio, které jsou plně podporovány.
 V době návrhu v sadě Visual Studio můžete použít obousměrných jazycích následujícími způsoby:

-   **Zadání textu** sady Visual Studio podporuje kódování Unicode, takže když systém je nastaven na odpovídající národní prostředí a jazyk, můžete zadat text ve arabské nebo hebrejské. (Arabské podpora zahrnuje kašidy a diakritických znamének.)

-   **Názvy objektů** obousměrných jazycích můžete přiřadit názvy řešení, projekty, soubory, složky a tak dále. V kódu můžete použít obousměrných jazycích pro názvy proměnných, tříd, objektů, atributy, metadata a další prvky.

-   **Kódování souboru** můžete ukládání a otevírání souborů s konkrétní jazyk nebo kódování Unicode. Další informace najdete v tématu [postupy: ukládání a otevírání souborů s kódováním](../ide/how-to-save-and-open-files-with-encoding.md).

## <a name="features-with-limited-or-no-support"></a>Funkce s omezením nebo bez podpory
 Další funkce, které jsou společné pro obousměrných jazyků aplikací nejsou plně podporovány v sadě Visual Studio nebo v některých případech se vůbec ne. Zde jsou některé z nich:

**Doleva pořadí čtení** ve výchozím nastavení, ovládací prvky zadání textu můžete použít v sadě Visual Studio používat pořadí čtení zleva doprava. Ve většině případů můžete použít standardní Windows gesta přepnout pořadí čtení. Například můžete stisknout **Ctrl + RightShift** přepnout **vlastnosti** okna pro podporu hodnoty vlastností pořadí čtení zprava doleva.

Pořadí čtení zprava doleva není ale podporované všude v sadě Visual Studio. Výjimky patří:

-   Zaškrtávací políčka, rozevírací seznamy a další ovládací prvky v dialogových oknech sady Visual Studio použijte vždy pořadí čtení zleva doprava.

-   Editor kódu (a textový editor) nepodporuje pořadí čtení zprava doleva. Můžete zadat text v obousměrných jazyků, ale je vždy o pořadí čtení zleva doprava.

## <a name="naming-things-using-arabic-or-hebrew-text"></a>Pojmenování věci pomocí arabský nebo hebrejský text
 Arabský nebo hebrejský text můžete přiřadit názvy složek, proměnné nebo jiné objekty. Při práci s arabština, můžete použít libovolný Arabské znaků včetně kašidy a diakritických znamének.

 Tyto prvky můžete být pojmenované pomocí arabské nebo hebrejské a se zpracuje správně v sadě Visual Studio:

-   Řešení, projektů a názvy souborů, včetně některou ze složek, které jsou v cestě projektu. **Průzkumník řešení** správně zobrazí řešení a názvy elementů.

-   Obsah souboru. Můžete otevřít nebo uložit soubory s kódováním Unicode nebo s vybranou znakovou stránkou.

    > [!NOTE]
    >  Editor kódu je zvláštní případ. Podrobnosti najdete níže.

-   Datové prvky. **Průzkumník serveru** správně zobrazí tyto prvky a bylo možné upravovat.

-   Prvky zkopírováno do schránky Windows.

-   Atributy a metadata.

-   Hodnoty vlastností. Arabský nebo hebrejský text v můžete použít **vlastnosti** okna. V okně umožňuje přepínat mezi pořadí čtení zprava doleva a doprava a doleva pomocí standardních klávesových úhozů Windows (**Ctrl + RightShift** pro right to left, a **Ctrl + LeftShift** pro zleva doprava).

-   Kód a text literálu. V editoru kódu (což je také textového editoru) vám pomůže arabské nebo hebrejské název třídy, funkce, proměnné, vlastnosti, řetězcové literály, atributy a tak dále. Editor ale nepodporuje pořadí čtení zprava doleva. text vždy začíná na levém okraji.

    > [!TIP]
    > Doporučujeme, umístěte řetězcové literály do souborů prostředků místo pevného kódování je do vašich aplikací. Další informace najdete v tématu [prostředky v aplikacích klasické pracovní plochy (.NET Framework)](/dotnet/framework/resources/index).

    > [!NOTE]
    > Musíte být konzistentní vzhledem k aplikacím v jak odkazovat na objekty s názvem v těchto jazycích. Pokud používáte kašidy názvů Arabské proměnné, musíte vždycky použít kašida k odkazování na tuto proměnnou nebo způsobí chyby.

-   Komentáře ke kódu. Vytvoření komentářů v arabské nebo hebrejské. Můžete také těchto jazyků v nástroji Tvůrce komentář.

## <a name="see-also"></a>Viz také:

- [Obousměrná podpora pro aplikace Windows Forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)
- [Obousměrná podpora pro webové aplikace ASP.NET](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)
- [Globalizace aplikací](../ide/globalizing-applications.md)
- [Lokalizace aplikací](../ide/localizing-applications.md)