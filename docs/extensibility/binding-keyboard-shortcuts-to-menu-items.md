---
title: Vazby klávesových zkratek na položky nabídky | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94feafbc614be61aaa4eef9e26669c0fbe901ed5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740020"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Svázání klávesových zkratek s položkami nabídky
Chcete-li svázat klávesovou zkratku s příkazem vlastní nabídky, stačí přidat položku do souboru *.vsct* pro balíček. Toto téma vysvětluje, jak mapovat klávesovou zkratku na vlastní tlačítko, položku nabídky nebo příkaz panelu nástrojů a jak použít mapování klávesnice ve výchozím editoru nebo omezit na vlastní editor.

 Informace o přiřazení klávesových zkratek k existujícím položkám nabídky sady Visual Studio naleznete v [tématu Identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="choose-a-key-combination"></a>Vyberte si kombinaci kláves
 Mnoho klávesových zkratek se již používá v sadě Visual Studio. Neměli byste přiřadit stejný zástupce více než jeden příkaz, protože duplicitní vazby jsou obtížné zjistit a může také způsobit nepředvídatelné výsledky. Proto je vhodné ověřit dostupnost zástupce před jeho přiřazením.

### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Ověření dostupnosti klávesové zkratky

1. V okně**Prostředí** **možností** >  **nástrojů** > vyberte **klávesy Klávesnice**.

2. Ujistěte se, že **je funkce Použít nový zástupce v** programu **Globální**.

3. Do pole **Stiskněte klávesové zkratky** zadejte klávesovou zkratku, kterou chcete použít.

    Pokud je zástupce již použit v sadě Visual Studio, zobrazí se v poli Zástupce aktuálně používaný v **aplikaci** Příkaz, který zástupce aktuálně volá.

4. Vyzkoušejte různé kombinace klíčů, dokud nenajdete ten, který není namapován.

   > [!NOTE]
   > Klávesové zkratky, které používají **alt,** mohou otevřít nabídku a ne přímo spustit příkaz. **Proto zástupce aktuálně používá** pole může být prázdné při zadání zástupce, který obsahuje **Alt**. Můžete ověřit, zda zástupce neotevře nabídku, zavřením dialogového okna **Možnosti** a stisknutím kláves.

   Následující postup předpokládá, že máte existující VSPackage s příkazem nabídky. Pokud potřebujete pomoc, podívejte se na [Vytvořit rozšíření s příkazem nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).

### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Přiřazení klávesové zkratky k příkazu

1. Otevřete soubor *.vsct* pro váš balíček.

2. Vytvořte `<KeyBindings>` prázdný oddíl `<Commands>` za if, který ještě není k dispozici.

   > [!WARNING]
   > Další informace o klíč vazby naleznete v [tématu Keybinding](../extensibility/keybinding-element.md).

    V `<KeyBindings>` části vytvořte `<KeyBinding>` položku.

    Nastavte `guid` atributy a `id` na atributy příkazu, který chcete vyvolat.

    Nastavte `mod1` atribut na **Control**, **Alt**nebo **Shift**.

    KeyBindings části by měl vypadat podobně:

   ```xml
   <KeyBindings>
       <KeyBinding guid="<name of command set>" id="<name of command id>"
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>
   </KeyBindings>

   ```

   Pokud klávesová zkratka vyžaduje více `mod2` než `key2` dvě klávesy, nastavte atributy a.

   Ve většině situací **shift** by neměl být používán bez druhého modifikátoru, protože stisknutím tohoto tlačítka již většina alfanumerických kláves zadá velké písmeno nebo symbol.

   Kódy virtuálních klíčů umožňují přístup ke speciálním klíčům, ke kterým není přidružen znak, například funkční klávesy a klávesa **Backspace.** Další informace naleznete v [tématu Virtual-key codes](/windows/desktop/inputdev/virtual-key-codes).

   Chcete-li příkaz zpřístupnit v editoru `editor` sady `guidVSStd97`Visual Studio, nastavte atribut na .

   Chcete-li příkaz zpřístupnit pouze ve vlastním `editor` editoru, nastavte atribut na název vlastního [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editoru, který byl vygenerován šablonou balíčku při vytváření balíčku, který obsahuje vlastní editor. Chcete-li najít hodnotu `<Symbols>` názvu, `<GuidSymbol>` vyhledejte `name` v části`editorfactory`uzel, jehož atribut končí na " . Toto je název vlastního editoru.

## <a name="example"></a>Příklad
 Tento příklad sváže klávesovou zkratku **Ctrl**+**Alt**+**C** s příkazem pojmenovaným `cmdidMyCommand` v balíčku s názvem `MyPackage`.

```
<CommandTable>
. . .
<Commands>
. . .
</Commands>
<KeyBindings>
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />
</KeyBindings>
. . .
</CommandTable>
```

## <a name="example"></a>Příklad
 Tento příklad sváže klávesovou zkratku **Ctrl**+**B** s příkazem pojmenovaným `cmdidBold` v projektu s názvem `TestEditor`. Příkaz je k dispozici pouze ve vlastním editoru a nikoli v jiných editorech.

```xml
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />
```

## <a name="see-also"></a>Viz také
- [Rozšíření nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
