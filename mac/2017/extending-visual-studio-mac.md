---
title: Rozšíření sady Visual Studio pro Mac
description: Visual Studio pro mac funkce a funkce lze rozšířit o moduly nazývané balíčky rozšíření. První část této příručky vytvoří jednoduchý balíček rozšíření Sady Visual Studio pro Mac pro vložení data a času do dokumentu. Druhá část této příručky představuje základy systému rozšíření balíčku a některé základní api, které tvoří základ Visual Studio pro Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 29c5bb9c45ae8d859316bd9c63eec10a6a425571
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851960"
---
# <a name="extending-visual-studio-for-mac"></a>Rozšíření sady Visual Studio pro Mac

Visual Studio pro Mac se skládá ze sady modulů s názvem *Balíčky rozšíření*. Balíčky rozšíření můžete použít k zavedení nových funkcí do Sady Visual Studio pro Mac, jako je například podpora pro další jazyk nebo novou šablonu projektu.

Rozšiřující balíčky sestavení z *rozšíření* bodů jiných balíčků rozšíření. Rozšiřující body jsou zástupné symboly pro oblasti, které lze rozbalit, jako je například nabídka nebo seznam příkazů IDE. Balíček rozšíření můžete sestavit z bodu rozšíření registrací uzlu strukturovaných dat nazývaných rozšíření, jako je například nová položka nabídky nebo nový příkaz. Každý přípojný bod přijímá určité typy rozšíření, například *Příkaz*, *Pad*nebo *FileTemplate*. Modul, který obsahuje rozšiřující body, se nazývá *hostitel doplňku*, protože jej lze rozšířit o další balíčky rozšíření.

Chcete-li přizpůsobit Visual Studio pro Mac, můžete vytvořit balíček rozšíření, který se staví z rozšiřujících bodů obsažených v hostitelích doplňků v rámci již existujících knihoven v sadě Visual Studio for Mac, jak ukazuje následující diagram:

![Architektura doplňku](media/extending-visual-studio-mac-addin1.png)

Aby balíček rozšíření k sestavení z Visual Studio pro Mac, musí mít rozšíření, které sestavení z již existující rozšíření bodů v rámci Visual Studio pro Mac IDE. Když balíček rozšíření spoléhá na bod rozšíření definované v hostiteli doplňku, říká se, že mají _závislost_ na tomto balíčku rozšíření.

Výhodou tohoto modulárního návrhu je, že Visual Studio pro Mac je rozšiřitelný – existuje mnoho rozšiřujících bodů, na kterých lze stavět pomocí vlastních balíčků rozšíření. Příklady aktuální balíčky rozšíření patří podpora pro C# a F#, ladicí nástroje a šablony projektu.

> [!NOTE]
> Pokud máte projekt Doplňku Maker, který byl vytvořen před doplňkem Maker 1.2, je třeba projekt migrovat, jak je uvedeno v [krocích zde](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Tato část se zabývá různými soubory generovanými doplňkem Maker a daty, která vyžaduje rozšíření příkazů.

## <a name="attribute-files"></a>Soubory atributů

Balíčky rozšíření ukládají metadata o jejich názvu, verzi, závislostech a dalších informacích v atributech jazyka C#. Tvůrce doplňků vytvoří dva soubory `AddinInfo.cs` `AssemblyInfo.cs` a uloží a uspořádá tyto informace. Balíčky rozšíření musí mít jedinečné id a obor názvů zadané v atributu *Addin*:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Balíčky rozšíření musí také deklarovat závislosti na balíčky rozšíření, které vlastní rozšíření bodů, které připojit. Tyto jsou automaticky odkazovány v době sestavení.

Kromě toho mohou být přidány další odkazy prostřednictvím referenčního uzlu doplňku v panelu řešení pro projekt, jak je znázorněno na následujícím obrázku:

![Snímek obrazovky S datem vložení](media/extending-visual-studio-mac-addin13.png)

Mají také jejich `assembly:AddinDependency` odpovídající atributy přidány v době sestavení. Jakmile metadata a deklarace závislostí jsou na místě, můžete se zaměřit na základní stavební bloky balíčku rozšíření.

## <a name="extensions-and-extension-points"></a>Rozšíření a prodlužovací body

Bod rozšíření je zástupný symbol, který definuje datovou strukturu (typ), zatímco rozšíření definuje data, která odpovídají struktuře určené určitým bodem rozšíření. Body rozšíření určují, jaký typ rozšíření mohou přijmout ve své deklaraci. Rozšíření jsou deklarována pomocí názvů typů nebo cest rozšíření. Viz [odkaz na bod rozšíření](https://github.com/mono/mono-addins/wiki/Extension-Points) pro podrobnější vysvětlení, jak vytvořit bod rozšíření, které potřebujete.

Architektura rozšiřujících a rozšiřujících bodů udržuje vývoj Visual Studia pro Mac rychlý a modulární.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Rozšíření příkazů

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Rozšíření příkazů jsou rozšíření, která odkazují na metody, které jsou volány při každém spuštění.

Rozšíření příkazů jsou definována přidáním položek do `/MonoDevelop/Ide/Commands` bodu rozšíření. Naše rozšíření jsme `Manifest.addin.xml` definovali pomocí následujícího kódu:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Příponeční uzel obsahuje atribut cesty, který určuje bod rozšíření, do `/MonoDevelop/Ide/Commands/Edit`kterého se zapojuje, v tomto případě . Navíc funguje jako nadřazený uzel command. Uzel Příkaz má následující atributy:

* **id** - Určuje identifikátor tohoto příkazu. Identifikátory příkazů musí být deklarovány jako členy výčtu a slouží k připojení příkazů k commanditems.
* **_label** - Text, který se má zobrazit v nabídkách.
* **_description** - Text, který se má zobrazit jako popis pro tlačítka panelu nástrojů.
* **defaultHandler** - Určuje `CommandHandler` třídu, která napájí příkaz

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Rozšíření CommandItem, které se `/MonoDevelop/Ide/MainMenu/Edit` zapojuje do prodlužovacího bodu, je demonstrováno v následujícím fragmentu kódu:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

A CommandItem umístí příkaz zadaný v jeho id atribut do nabídky. Tato položka příkazu `/MonoDevelop/Ide/MainMenu/Edit` rozšiřuje bod rozšíření, což způsobí, že se popisek příkazu zobrazí v **nabídce Úpravy**. Všimněte si, že **id** v CommandItem odpovídá id `InsertDate`uzlu Příkaz , . Pokud byste příkazovou položku odebrali, možnost **Vložit datum** by z nabídky Úpravzmizela.

### <a name="command-handlers"></a>Obslužné rutiny příkazů

Je `InsertDateHandler` rozšíření třídy. `CommandHandler` Přepíše dvě metody `Update` `Run`a . Metoda `Update` je dotazován vždy, když příkaz je zobrazen v nabídce nebo provedeny pomocí klíče vazby. Změnou objektu info můžete příkaz zakázat nebo jej zneviditelnit, naplnit příkazy pole a další. Tato `Update` metoda zakáže příkaz, pokud nemůže najít aktivní *dokument* s *TextEditor* vložit text do:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Metodu je třeba `Update` přepsat pouze v případě, že máte zvláštní logiku pro povolení nebo skrytí příkazu. Metoda `Run` se spustí vždy, když uživatel provede příkaz, který v tomto případě nastane, když uživatel vybere příkaz z nabídky Upravit. Tato metoda vloží datum a čas na stříšku v textovém editoru:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Deklarujte typ příkazu jako `DateInserterCommands`člen výčtu v rámci aplikace :

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Tím se spojí příkaz a commanditem - CommandItem volá příkaz, když je commanditem vybrán a **v nabídce Upravit**.

## <a name="ide-apis"></a>IDE API

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Informace o rozsahu oblastí, které jsou k dispozici pro vývoj, naleznete v [rozšíření tree reference](https://www.monodevelop.com/developers/articles/extension-tree-reference/) a přehled rozhraní [API](https://www.monodevelop.com/developers/articles/api-overview/). Při vytváření pokročilých rozšiřujících balíčků se také podívejte na [články pro vývojáře](https://www.monodevelop.com/developers/articles/). Níže je částečný seznam oblastí pro přizpůsobení:

* Podložky
* Klíčová vazebná schémata
* Zásady
* Kód formatters
* Formáty souborů projektu
* Panely předvoleb
* Panely možností
* Protokoly ladicího programu
* Vizualizéry ladicího programu
* Rozložení pracovního prostoru
* Uzly stromu podložky řešení
* Okraje zdrojového editoru
* Zkušební motory pro jednotku
* Generátory kódů
* Fragmenty kódu
* Cílové architektury
* Cílový čas běhu
* VCS back-endy
* Refaktoring
* Obslužné rutiny spuštění
* Zvýraznění syntaxe

## <a name="additional-information"></a>Další informace

> [!NOTE]
> V současné době pracujeme na vylepšení scénářů rozšiřitelnosti pro Visual Studio for Mac. Pokud vytváříte rozšíření a potřebujete další pomoc nebo informace nebo chcete poskytnout zpětnou vazbu, vyplňte prosím formulář [pro vytváření rozšíření Sady Visual Studio pro Mac.](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u)

## <a name="see-also"></a>Viz také

- [Vývoj rozšíření visual studia (ve Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
