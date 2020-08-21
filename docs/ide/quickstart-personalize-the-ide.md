---
title: Použití tmavého motivu a změna barvy textu v editoru
description: Naučte se, jak nastavit výchozí barevný motiv sady Visual Studio na tmavý režim a změnit barvy písma v textovém editoru.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperfq1
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3b0e7b11fae63b9a2233b7391805760d3fdd7d27
ms.sourcegitcommit: cf5b5437f0b43c6d52c479e1a2c443338bd27cda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2020
ms.locfileid: "88724923"
---
# <a name="how-to-personalize-the-visual-studio-ide-and-text-editor"></a>Postupy: přizpůsobení rozhraní IDE a textového editoru sady Visual Studio

V tomto článku s postupem se přizpůsobí barevný motiv sady Visual Studio výběrem tmavého motivu. Také přizpůsobíme barvy pro dva různé typy textu v textovém editoru.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="set-the-color-theme-for-the-ide"></a>Nastavení barevného motivu pro IDE

Výchozí barevný motiv pro uživatelské rozhraní sady Visual Studio se nazývá **modrý**. Pojďme změnit na **tmavě**.

1. Na panelu nabídek, který je řádek nabídek, jako je například **soubor** a **Úpravy**, vyberte možnost **nástroje**  >  **Options**.

1. Na stránce **Environment**  >  **Obecné** možnosti prostředí změňte výběr **barevného motivu** na **tmavý**a pak zvolte **OK**.

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

1. V dialogovém okně **nový soubor** v kategorii **Obecné** zvolte možnost **soubor XML**a pak zvolte možnost **otevřít**.

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

1. Chcete-li otevřít dialogové okno **Možnosti** , v řádku nabídek vyberte možnost **nástroje**  >  **Options** .

1. V části **prostředí**vyberte kategorii **písma a barvy** .

   Všimněte si, že text v části **Zobrazit nastavení pro** říká **textový editor** &mdash; je to, co chceme. Rozbalením rozevíracího seznamu jenom zobrazíte rozsáhlý seznam míst, kde můžete přizpůsobit písma a barvu textu.

1. Chcete-li změnit barvu textu čísel řádků, v seznamu **Zobrazit položky** vyberte položku **číslo řádku**. V poli **položka v popředí** vyberte možnost **olivová**.

   ![Dialogové okno Možnosti, kategorie písma a barvy](media/quickstart-personalize-line-number-color.png)

   Některé jazyky mají vlastní konkrétní nastavení písem a barev. Pokud jste vývojář C++ a chcete změnit barvu použitou pro funkce, například můžete vyhledat **funkce jazyka c++** v seznamu **položek zobrazení** .

1. Než se pustíte do dialogového okna, můžeme také změnit barvu atributů XML. V seznamu **položky zobrazení** přejděte dolů na **atribut XML** a vyberte jej. V poli **položka v popředí** vyberte položku **vápno**. Kliknutím na **tlačítko OK** uložte vybrané možnosti a zavřete dialogové okno.

   Čísla řádků jsou nyní barvou oliv a atributy XML jsou jasně zelená. Pokud otevřete jiný typ souboru, například soubor kódu C++ nebo C#, uvidíte, že čísla řádků se zobrazí také v barvě olivového oleje.

   ![Soubor XML s novými barvami písma](media/quickstart-personalize-xml-file-new-colors.png)

Prozkoumali jsme pouze několik způsobů přizpůsobení barev v aplikaci Visual Studio. Doufáme, že prozkoumáte další možnosti vlastního nastavení v dialogovém okně **Možnosti** , abyste mohli aplikaci Visual Studio skutečně dělat sami.

## <a name="see-also"></a>Viz také

- [Změna písem, barev a možností vysokého kontrastu v aplikaci Visual Studio](../ide/how-to-change-fonts-and-colors-in-visual-studio.md)
- [Přizpůsobení editoru](../ide/how-to-change-text-case-in-the-editor.md)
- [Integrované vývojové prostředí sady Visual Studio – přehled](../get-started/visual-studio-ide.md)
