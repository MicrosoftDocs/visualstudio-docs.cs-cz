---
title: Nastavení barevného motivu a písem
ms.date: 11/20/2017
ms.topic: quickstart
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039e48dec17ce902932e2d0df26ebb336c396985
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667789"
---
# <a name="personalize-the-visual-studio-ide-and-editor"></a>Přizpůsobení integrovaného vývojového prostředí a editoru sady Visual Studio

V tomto kurzu 5-10 minut přizpůsobíme barevný motiv sady Visual Studio tak, že vyberete tmavý motiv. Také přizpůsobíme barvy pro dva různé typy textu v textovém editoru.

::: moniker range="vs-2017"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a nainstalujte si ji zdarma.

::: moniker-end

::: moniker range=">=vs-2019"

Pokud jste ještě nenainstalovali Visual Studio, navštivte stránku [ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a nainstalujte si ji zdarma.

::: moniker-end

## <a name="set-the-color-theme"></a>Nastavení barevného motivu

Výchozí barevný motiv pro uživatelské rozhraní sady Visual Studio se nazývá **modrý**. Pojďme změnit na **tmavě**.

1. Na panelu nabídek, který je řádek nabídek, jako je například **soubor** a **Úpravy**, vyberte **nástroje**  > **Možnosti**.

1. Na stránce **prostředí**  > **Obecné** možnosti změňte výběr **barevného motivu** na **tmavý**a pak zvolte **OK**.

   Barevný motiv pro celé vývojové prostředí (IDE) sady Visual Studio se změní na **tmavý**.

   ::: moniker range="vs-2017"

   ![Visual Studio 2017 v tmavém motivu](media/quickstart-personalize-dark-theme.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![Visual Studio 2019 v tmavém motivu](media/vs-2019/dark-theme.png)

   ::: moniker-end

> [!TIP]
> Můžete nainstalovat další předdefinované motivy tím, že z [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)nainstalujete **Editor barevných motivů sady Visual Studio** . Po instalaci tohoto nástroje se v rozevíracím seznamu **barevný motiv** zobrazí další barevné motivy.

## <a name="change-text-color"></a>Změna barvy textu

Teď přizpůsobíme některé barvy textu pro Editor. Nejprve vytvoříme nový soubor XML pro zobrazení výchozích barev.

1. V řádku nabídek vyberte **soubor**  > **Nový**  > **soubor**.

1. V dialogovém okně **nový soubor** v kategorii **Obecné** zvolte možnost **soubor XML**a pak zvolte možnost **otevřít**.

1. Vložte následující kód XML pod řádek, který obsahuje `<?xml version="1.0" encoding="utf-8"?>`.

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

   Všimněte si, že čísla řádků představují tyrkysovou modrou barvu a atributy XML (například `id="bk101"`) jsou světle modrá barva. Pro tyto položky se změní barva textu.

   ![Barvy písma souboru XML](media/quickstart-personalize-xml-file.png)

1. Chcete-li otevřít dialogové okno **Možnosti** , v řádku nabídek vyberte možnost **nástroje**  > **Možnosti** .

1. V části **prostředí**vyberte kategorii **písma a barvy** .

   Všimněte si, že text v části **Zobrazit nastavení pro** říká **textový editor** &mdash;this je to, co chceme. Rozbalením rozevíracího seznamu jenom zobrazíte rozsáhlý seznam míst, kde můžete přizpůsobit písma a barvu textu.

1. Chcete-li změnit barvu textu čísel řádků, v seznamu **Zobrazit položky** vyberte položku **číslo řádku**. V poli **položka v popředí** vyberte možnost **olivová**.

   ![Dialogové okno Možnosti, kategorie písma a barvy](media/quickstart-personalize-line-number-color.png)

   Některé jazyky mají vlastní konkrétní nastavení písem a barev. Pokud jste C++ vývojář a chcete změnit barvu použitou pro funkce, například můžete hledat  **C++ funkce** v seznamu **položky zobrazení** .

1. Než se pustíte do dialogového okna, můžeme také změnit barvu atributů XML. V seznamu **položky zobrazení** přejděte dolů na **atribut XML** a vyberte jej. V poli **položka v popředí** vyberte položku **vápno**. Kliknutím na **tlačítko OK** uložte vybrané možnosti a zavřete dialogové okno.

   Čísla řádků jsou nyní barvou oliv a atributy XML jsou jasně zelená. Pokud otevřete jiný typ souboru, například C++ nebo C# soubor kódu, uvidíte, že čísla řádků se zobrazí také v barvě olivového oleje.

   ![Soubor XML s novými barvami písma](media/quickstart-personalize-xml-file-new-colors.png)

Prozkoumali jsme pouze několik způsobů přizpůsobení barev v aplikaci Visual Studio. Doufáme, že prozkoumáte další možnosti vlastního nastavení v dialogovém okně **Možnosti** , abyste mohli aplikaci Visual Studio skutečně dělat sami.

## <a name="see-also"></a>Viz také:

- [Přizpůsobení editoru](../ide/how-to-change-text-case-in-the-editor.md)
- [Integrované vývojové prostředí sady Visual Studio – přehled](../get-started/visual-studio-ide.md)