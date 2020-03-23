---
title: Nástroje pro lokalizaci
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9c6934c816574796d59f978c3d2f37f590cf578
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565120"
---
# <a name="develop-globalized-and-localized-apps"></a>Vývoj globalizovaných a lokalizovaných aplikací

Visual Studio usnadňuje vývoj pro mezinárodní publikum využitím služeb integrovaných do [rozhraní .NET](/dotnet/standard/globalization-localization/).

Například systém projektu pro aplikace Windows Forms můžete generovat soubory prostředků pro záložní jazykovou verzi operačního prostředí a každé další jazykové verze ui. Při vytváření projektu v sadě Visual Studio jsou soubory prostředků kompilovány z formátu XML sady Visual Studio (.resx) do zprostředkujícího binárního formátu (.resources), které jsou pak vloženy do satelitních sestavení. Další informace naleznete [v tématu Resource files v sadě Visual Studio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles) a vytvoření [satelitních sestavení pro desktopové aplikace](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps).

## <a name="bidirectional-languages"></a>Obousměrné jazyky

Pomocí sady Visual Studio můžete vytvářet aplikace, které správně zobrazují text v jazycích psaných zprava doleva, včetně arabštiny a hebrejštiny. U některých funkcí můžete jednoduše nastavit vlastnosti. V ostatních případech je nutné implementovat funkce v kódu.

> [!NOTE]
> Chcete-li zadávat a zobrazovat obousměrné jazyky, musíte pracovat s verzí systému Windows, která je nakonfigurována s příslušným jazykem. Může se jedná buď o anglickou verzi systému Windows s nainstalovanou příslušnou jazykovou sadou, nebo o vhodně lokalizovanou verzi systému Windows.

### <a name="apps-that-support-bidirectional-languages"></a>Aplikace, které podporují obousměrné jazyky

- Aplikace pro Windows

   Můžete vytvářet plně obousměrné aplikace, které zahrnují podporu obousměrného textu, pořadí čtení zprava doleva a zrcadlení (obrácení rozložení oken, nabídek, dialogových oken a tak dále). S výjimkou zrcadlení jsou tyto funkce k dispozici ve výchozím nastavení nebo jako nastavení vlastností. Zrcadlení je podporováno ze své podstaty pro některé funkce, jako jsou například okna se zprávami. V ostatních případech však je nutné implementovat zrcadlení v kódu. Další informace naleznete [v tématu obousměrná podpora aplikací windows forms](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications).

- Webové aplikace

   Webové služby podporují odesílání a přijímání textu UTF-8 a Unicode, takže jsou vhodné pro aplikace, které zahrnují obousměrné jazyky. Webové klientské aplikace spoléhají na prohlížeče pro své uživatelské rozhraní, takže stupeň obousměrné podpory ve webové aplikaci závisí na tom, jak dobře prohlížeč uživatele podporuje tyto obousměrné funkce. V sadě Visual Studio můžete vytvářet aplikace s podporou arabského nebo hebrejského textu, pořadí čtení zprava doleva, kódování souborů a nastavení místní jazykové verze. Další informace naleznete [v tématu Obousměrná podpora ASP.NET webových aplikací](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03).

> [!NOTE]
> Konzolové aplikace neobsahují podporu textu pro obousměrné jazyky. To je důsledkem toho, jak systém Windows pracuje s konzolovými aplikacemi.

## <a name="see-also"></a>Viz také

- [Podpora obousměrných jazyků v sadě Visual Studio](use-bidirectional-languages.md)
- [Globalizace a lokalizaci aplikací .NET](/dotnet/standard/globalization-localization/)
- [Prostředky v aplikacích .NET](/dotnet/framework/resources/)
