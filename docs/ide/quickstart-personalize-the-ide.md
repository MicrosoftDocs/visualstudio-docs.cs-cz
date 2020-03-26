---
title: Nastavení barevného motivu a písem
ms.date: 03/23/2020
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c0b7b4e439f33e4e2eed8609d7e85e098068aea
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233155"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Přizpůsobení rozhraní IDE a editoru sady Visual Studio

V tomto 5-10 minutovém kurzu přizpůsobíme barevný motiv visual ateliu výběrem tmavého motivu. V textovém editoru také přizpůsobíme barvy pro dva různé typy textu.

::: moniker range="vs-2017"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste visual studio ještě nenainstalovali, přejděte na stránku [ke stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte ji zdarma.

::: moniker-end

## <a name="set-the-color-theme"></a>Nastavení barevného motivu

Výchozí barevný motiv pro uživatelské rozhraní sady Visual Studio se nazývá **Modrá**. Změníme to na **Dark**.

1. Na řádku nabídek, což je řádek nabídek, jako je **Soubor** a **Úpravy**, zvolte**Možnosti** **nástrojů** > .

1. Na stránce**Volby Obecné** **prostředí** > změňte výběr **motivu Barva** na **Tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí sady Visual Studio (IDE) se změní na **Tmavý**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 v tmavém motivu](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Další předdefinované motivy můžete nainstalovat instalací **Editoru barevných motivů sady Visual Studio** z [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Po instalaci tohoto nástroje se v rozevíracím seznamu **Barevný motiv** zobrazí další barevné motivy.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Vlastní motivy můžete vytvořit instalací **Návrháře motivů barev sady Visual Studio** z webu Visual Studio [Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

::: moniker-end

## <a name="change-text-color"></a>Změna barvy textu

Nyní přizpůsobíme některé barvy textu pro editor. Nejprve vytvoříme nový soubor XML, abyse zobcely výchozí barvy.

1. V řádku nabídek zvolte **Soubor** > **nový** > **soubor**.

1. V dialogovém okně **Nový soubor** vyberte v kategorii **Obecné** **soubor XML**a pak zvolte **Otevřít**.

1. Pod řádek, který obsahuje `<?xml version="1.0" encoding="utf-8"?>`, vložte následující kód XML.

   ```xml
   <Catalog>
     <Book id="bk101">
     <Author>Garghentini, Davide</Author>
     <Title>XML Developer's Guide</Title>
     <Genre>Computer</Genre>
     <Price>44.95</Price>
     <PublishDate>2000-10-01</PublishDate>
     <Description>
       An in-depth look at creating applications with XML.
     </Description>
   </Book>
   <Book id="bk102">
     <Author>Garcia, Debra</Author>
     <Title>Midnight Rain</Title>
     <Genre>Fantasy</Genre>
     <Price>5.95</Price>
     <PublishDate>2000-12-16</PublishDate>
     <Description>
       A former architect battles corporate zombies, an evil
       sorceress, and her own childhood to become queen of the world.
     </Description>
   </Book>
   </Catalog>
   ```

   Všimněte si, že čísla řádků jsou tyrkysově modrá barva `id="bk101"`a atributy XML (například) jsou světle modré barvy. Změníme barvu textu pro tyto položky.

   ![Barvy písma souboru XML](media/quickstart-personalize-xml-file.png)

1. Chcete-li otevřít dialogové okno **Volby,** zvolte**Možnosti** **nástrojů** > z řádku nabídek.

1. V části **Prostředí**zvolte kategorii **Písma a barvy.**

   Všimněte si, že text v části **Zobrazit nastavení pro** říká Textový **editor**&mdash;to je to, co chceme. Rozbalte rozevírací seznam, abyste viděli rozsáhlý seznam míst, kde můžete přizpůsobit písma a barvu textu.

1. Chcete-li změnit barvu textu čísel řádků, zvolte v seznamu **Zobrazit položky** **číslo řádku**. V poli **Popředí položky** zvolte **Oliva**.

   ![Dialogové okno Volby, kategorie Písma a Barvy](media/quickstart-personalize-line-number-color.png)

   Některé jazyky mají vlastní specifické nastavení písem a barev. Pokud jste vývojář jazyka C++ a chcete změnit barvu použitou pro funkce, můžete například vyhledat **funkce jazyka C++** v seznamu **Zobrazit položky.**

1. Než vystoupíme z dialogového okna, změníme také barvu atributů XML. V seznamu **Zobrazit položky** přejděte dolů na **Atribut XML** a vyberte ho. V poli **Položka popředí** zvolte **Vápno**. Chcete-li uložit naše výběry, zvolte **OK** a zavřete dialogové okno.

   Čísla řádků jsou nyní olivová barva a atributy XML jsou jasně, limetkově zelené. Pokud otevřete jiný typ souboru, například soubor kódu C++ nebo C#, uvidíte, že čísla řádků se také zobrazí v olivové barvě.

   ![Soubor XML s novými barvami písma](media/quickstart-personalize-xml-file-new-colors.png)

Prozkoumali jsme jen několik způsobů přizpůsobení barev v sadě Visual Studio. Doufáme, že prozkoumáte další možnosti přizpůsobení v dialogovém okně **Možnosti,** abyste visual studio skutečně vytvořili jako svůj vlastní.

## <a name="see-also"></a>Viz také

- [Přizpůsobení editoru](../ide/how-to-change-text-case-in-the-editor.md)
- [Integrované vývojové prostředí sady Visual Studio – přehled](../get-started/visual-studio-ide.md)
