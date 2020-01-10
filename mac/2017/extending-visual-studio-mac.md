---
title: Rozšíření sady Visual Studio pro Mac
description: Funkce a funkce Visual Studio pro Mac lze rozšířit pomocí modulů nazývaných balíčky rozšíření. První část této příručky vytvoří jednoduchý balíček rozšíření Visual Studio pro Mac pro vložení data a času do dokumentu. Druhá část tohoto průvodce zavádí základní informace o systému balíčku rozšíření a některých základních rozhraní API, která tvoří základ Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 29c5bb9c45ae8d859316bd9c63eec10a6a425571
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851960"
---
# <a name="extending-visual-studio-for-mac"></a>Rozšíření sady Visual Studio pro Mac

Visual Studio pro Mac sestávají ze sady modulů označované jako *balíčky rozšíření*. Balíčky rozšíření můžete použít k zavedení nových funkcí Visual Studio pro Mac, jako je například podpora pro další jazyk nebo novou šablonu projektu.

Balíčky rozšíření se sestavují z bodů *rozšíření* jiných balíčků rozšíření. Rozšiřovací body jsou zástupné symboly pro oblasti, které lze rozbalit, jako je například nabídka nebo seznam příkazů rozhraní IDE. Balíček rozšíření může být sestaven z rozšiřujícího bodu tím, že registruje uzel strukturovaných dat, který se nazývá rozšíření, jako je například nová položka nabídky nebo nový příkaz. Každý bod rozšíření přijímá určité typy rozšíření, jako je například *příkaz*, *panel*nebo *Šablona*souborů. Modul, který obsahuje Rozšiřovací body, se nazývá *hostitel doplňku*, protože ho lze rozšířit jinými balíčky rozšíření.

Chcete-li přizpůsobit Visual Studio pro Mac, můžete vytvořit balíček rozšíření, který sestaví z bodů rozšíření obsažených v hostitelích doplňku v rámci existujících knihoven v Visual Studio pro Mac, jak je znázorněno na následujícím obrázku:

![Architektura doplňku](media/extending-visual-studio-mac-addin1.png)

Aby balíček rozšíření mohl sestavovat z Visual Studio pro Mac, musí mít rozšíření, která se sestavují z již existujících rozšiřovacích bodů v rámci Visual Studio pro Mac integrovaného vývojového prostředí (IDE). Pokud balíček rozšíření spoléhá na bod rozšíření definovaný v hostiteli doplňku, označuje se jako _závislost_ v tomto balíčku rozšíření.

Výhodou tohoto modulárního návrhu je, že Visual Studio pro Mac rozšiřitelné – existuje mnoho rozšiřujících bodů, které mohou být postaveny s vlastními balíčky rozšíření. Příklady aktuálních balíčků rozšíření zahrnují podporu nástrojů C# a F#, ladicích programů a šablon projektů.

> [!NOTE]
> Máte-li k dispozici projekt doplňku doplňku, který byl vytvořen před doplňkem Tvůrce 1,2, je třeba migrovat projekt, jak je uvedeno v [tomto postupu.](https://mhut.ch/addinmaker/1.2)

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

V této části jsou popsány různé soubory generované doplňkem pro tvůrce a data, která vyžaduje rozšíření příkazů.

## <a name="attribute-files"></a>Soubory atributů

Balíčky rozšíření ukládají metadata týkající se jejich názvu, verze, závislostí a dalších informací C# v atributech. Tvůrce doplňku vytvoří dva soubory `AddinInfo.cs` a `AssemblyInfo.cs` k ukládání a uspořádání těchto informací. Balíčky rozšíření musí mít jedinečné ID a obor názvů, které jsou zadané v *atributu AddIn*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Balíčky rozšíření musí také deklarovat závislosti na balíčcích rozšíření, které vlastní body rozšíření, které se připojují k. Tyto jsou automaticky odkazovány v době sestavení.

Kromě toho je možné přidat další odkazy prostřednictvím uzlu reference doplňku na panelu řešení pro projekt, jak je znázorněno na následujícím obrázku:

![Snímek obrazovky pro vložení data](media/extending-visual-studio-mac-addin13.png)

Mají také odpovídající atributy `assembly:AddinDependency` přidány v době sestavení. Jakmile jsou deklarace metadat a závislostí na místě, můžete se zaměřit na základní stavební kameny balíčku rozšíření.

## <a name="extensions-and-extension-points"></a>Rozšíření a rozšiřovací body

Rozšiřovací bod je zástupný symbol, který definuje datovou strukturu (typ), zatímco rozšíření definuje data, která jsou v souladu se strukturou určenou konkrétním rozšiřovacím bodem. Rozšiřovací body určují, jaký typ rozšíření můžou v deklaraci přijmout. Rozšíření jsou deklarována pomocí názvů typů nebo cest rozšíření. Podrobnější vysvětlení, jak vytvořit rozšiřující bod, najdete v [referenčních informacích k rozšiřujícímu bodu](https://github.com/mono/mono-addins/wiki/Extension-Points) .

Architektura rozšíření/rozšiřovacího bodu udržuje vývoj Visual Studio pro Mac rychlý a modulární.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozšíření příkazů

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Rozšíření příkazů jsou rozšíření, která odkazují na metody, které jsou volány pokaždé, když je spuštěn.

Rozšíření příkazů jsou definována přidáním položek do bodu rozšíření `/MonoDevelop/Ide/Commands`. V `Manifest.addin.xml` jsme toto rozšíření definovali pomocí následujícího kódu:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Uzel rozšíření obsahuje atribut path, který určuje rozšiřovací bod, do kterého je zapojen, v tomto případě `/MonoDevelop/Ide/Commands/Edit`. Kromě toho funguje jako nadřazený uzel pro příkaz. Uzel příkazu má následující atributy:

* **ID** – Určuje identifikátor pro tento příkaz. Identifikátory příkazů musí být deklarovány jako členy výčtu a použity pro připojení příkazů k CommandItems.
* **_label** – text, který se má zobrazit v nabídkách
* **_description** – text, který má být zobrazen jako popis tlačítka panelu nástrojů.
* **defaultHandler** – určuje třídu `CommandHandler`, která je založená na příkazu.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

CommandItem rozšíření, které se připojuje k bodu rozšíření `/MonoDevelop/Ide/MainMenu/Edit`, je znázorněno v následujícím fragmentu kódu:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem umístí příkaz zadaný v atributu ID do nabídky. Tento CommandItem rozšiřuje bod rozšíření `/MonoDevelop/Ide/MainMenu/Edit`, který umožňuje zobrazení popisku příkazu v **nabídce Úpravy**. Všimněte si, že **ID** v CommandItem odpovídá ID uzlu příkazu, `InsertDate`. Pokud jste chtěli odebrat CommandItem, možnost **Vložit datum** by v nabídce Úpravy zmizela.

### <a name="command-handlers"></a>Obslužné rutiny příkazů

`InsertDateHandler` je rozšíření `CommandHandler` třídy. Přepisuje dvě metody `Update` a `Run`. Metoda `Update` se dotazuje vždy, když se v nabídce zobrazí příkaz nebo se spustí prostřednictvím vazeb kláves. Změnou objektu info můžete zakázat příkaz nebo ho nastavit jako neviditelný, vyplnit pole a další. Tato metoda `Update` zakáže příkaz, pokud nemůže najít aktivní *dokument* s *TextEditor* , do kterého se má vložit text:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Metodu `Update` musíte přepsat pouze v případě, že máte speciální logiku pro povolení nebo skrytí příkazu. Metoda `Run` se spustí pokaždé, když uživatel spustí příkaz, což v tomto případě nastane, když uživatel vybere příkaz z nabídky upravit. Tato metoda vloží datum a čas na blikající kurzor v textovém editoru:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Deklarace typu příkazu jako člena výčtu v rámci `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Tento příkaz spojí příkazy a CommandItem – CommandItem volá příkaz při výběru CommandItem z **nabídky upravit**.

## <a name="ide-apis"></a>Rozhraní API IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Informace o rozsahu oblastí, které jsou k dispozici pro vývoj, naleznete v tématu [reference stromu rozšíření](https://www.monodevelop.com/developers/articles/extension-tree-reference/) a [Přehled rozhraní API](https://www.monodevelop.com/developers/articles/api-overview/). Při sestavování pokročilých balíčků rozšíření si taky Přečtěte [článek věnované vývojářům](https://www.monodevelop.com/developers/articles/). Níže je uveden částečný seznam oblastí pro přizpůsobení:

* Chrániče
* Schémata vazeb klíčů
* Zásady
* Formátování kódu
* Formáty souborů projektu
* Panely předvoleb
* Panely možností
* Protokoly ladicího programu
* Nástroje pro vizualizace ladicího programu
* Rozložení pracovního prostoru
* Uzly stromu panelu řešení
* Okraje editoru zdrojového kódu
* Stroje pro testování částí
* Generátory kódu
* Fragmenty kódu
* Cílové architektury
* Cílový modul runtime
* Back-endy VCS
* Refaktoring
* Obslužné rutiny spuštění
* Zvýrazňování syntaxe

## <a name="additional-information"></a>Další informace

> [!NOTE]
> V současné době pracujeme na vylepšení scénářů rozšíření pro Visual Studio pro Mac. Pokud vytváříte rozšíření a potřebujete další pomoc nebo informace, nebo chcete poskytnout zpětnou vazbu, vyplňte prosím formulář pro [vytváření rozšíření Visual Studio pro Mac](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) .

## <a name="see-also"></a>Viz také:

- [Vývoj rozšíření sady Visual Studio (ve Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
