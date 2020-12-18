---
title: Nastavení tmavého motivu sady Visual Studio a změna barev textu
description: Naučte se, jak změnit výchozí barevný motiv sady Visual Studio na tmavý režim a změnit barvy písma v editoru kódu.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d261d6c13572be6df80ca36f37e19792d53e2a32
ms.sourcegitcommit: c558d8a0f02ed2c932c8d6f70756d8d2cedb10b3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97684036"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-the-editor"></a>Postupy: Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio a editoru

V tomto článku s postupem budeme přizpůsobovat barevný motiv sady Visual Studio z výchozího modrého motivu na tmavý motiv. Pak přizpůsobíme barvy pro dva různé typy textu v editoru kódu.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Nastavení barevného motivu pro IDE

Výchozí barevný motiv pro uživatelské rozhraní sady Visual Studio se nazývá **modrý**. Pojďme změnit na **tmavě**.

1. Na panelu nabídek, který je řádek nabídek, jako je například **soubor** a **Úpravy**, vyberte možnost **nástroje**  >  .

1. Na stránce   >  **Obecné** možnosti prostředí změňte výběr **barevného motivu** na **tmavý** a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí (IDE) sady Visual Studio se změní na **tmavý**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 v tmavém motivu](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

::: moniker range="vs-2017"

> [!TIP]
> Můžete nainstalovat další předdefinované motivy tím, že z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)nainstalujete **Editor barevných motivů sady Visual Studio** . Po instalaci tohoto nástroje se v rozevíracím seznamu **barevný motiv** zobrazí další barevné motivy.

::: moniker-end

::: moniker range="vs-2019"

> [!TIP]
> Můžete vytvořit vlastní motivy tím, že z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)nainstalujete **Návrháře barevných motivů sady Visual Studio** .

::: moniker-end

## <a name="change-text-colors-in-the-editor"></a>Změna barev textu v editoru

Teď přizpůsobíme některé barvy textu pro Editor. Nejprve vytvoříme nový soubor XML pro zobrazení výchozích barev.

1. V řádku nabídek vyberte **soubor**  >  **Nový**  >  **soubor**.

1. V dialogovém okně **nový soubor** v kategorii **Obecné** zvolte možnost **soubor XML** a pak zvolte možnost **otevřít**.

1. Vložte následující kód XML pod řádek, který obsahuje `<?xml version="1.0" encoding="utf-8"?>` .

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

   Všimněte si, že čísla řádků jsou tyrkysově modrá barva a atributy XML (například `id="bk101"` ) jsou světle modrá barva. Pro tyto položky se změní barva textu.

   ![Barvy písma souboru XML](media/quickstart-personalize-xml-file.png)

1. Chcete-li otevřít dialogové okno **Možnosti** , v řádku nabídek vyberte možnost **nástroje**  >   .

1. V části **prostředí** vyberte kategorii **písma a barvy** .

   Všimněte si, že text v části **Zobrazit nastavení pro** říká **textový editor** &mdash; je to, co chceme. Rozbalením rozevíracího seznamu jenom zobrazíte rozsáhlý seznam míst, kde můžete přizpůsobit písma a barvu textu.

1. Chcete-li změnit barvu textu čísel řádků, v seznamu **Zobrazit položky** vyberte položku **číslo řádku**. V poli **položka v popředí** vyberte možnost **olivová**.

   ![Dialogové okno Možnosti, kategorie písma a barvy](media/quickstart-personalize-line-number-color.png)

   Některé jazyky mají vlastní konkrétní nastavení písem a barev. Pokud jste vývojář C++ a chcete změnit barvu použitou pro funkce, například můžete vyhledat **funkce jazyka c++** v seznamu **položek zobrazení** .

1. Než se pustíte do dialogového okna, můžeme také změnit barvu atributů XML. V seznamu **položky zobrazení** přejděte dolů na **atribut XML** a vyberte jej. V poli **položka v popředí** vyberte položku **vápno**. Kliknutím na **tlačítko OK** uložte vybrané možnosti a zavřete dialogové okno.

   Čísla řádků jsou nyní barvou oliv a atributy XML jsou jasně zelená. Pokud otevřete jiný typ souboru, například soubor kódu C++ nebo C#, uvidíte, že čísla řádků se zobrazí také v barvě olivového oleje.

   ![Soubor XML s novými barvami písma](media/quickstart-personalize-xml-file-new-colors.png)

Prozkoumali jsme pouze několik způsobů přizpůsobení barev v aplikaci Visual Studio. Doufáme, že prozkoumáte další možnosti vlastního nastavení v dialogovém okně [**Možnosti**](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) , abyste mohli aplikaci Visual Studio skutečně dělat sami.

## <a name="see-also"></a>Viz také

- [Postupy: Změna písma, barev a motivů v aplikaci Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Postupy: Změna velikosti písmen textu v editoru](../ide/how-to-change-text-case-in-the-editor.md)
- [Přehled integrovaného vývojového prostředí sady Visual Studio](../get-started/visual-studio-ide.md)
