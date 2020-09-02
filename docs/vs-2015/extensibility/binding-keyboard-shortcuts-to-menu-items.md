---
title: Vázání klávesových zkratek k položkám nabídky | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0396d3290ef870fb2c2c7b7b49c774b66397077c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852219"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Vytváření vazeb mezi klávesovými zkratkami a položkami nabídky
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li vytvořit novou klávesovou zkratku pro vlastní příkaz nabídky, stačí přidat položku do souboru. vsct pro balíček. Toto téma vysvětluje, jak namapovat klávesovou zkratku na vlastní tlačítko, položku nabídky nebo příkaz panelu nástrojů a jak použít mapování klávesnice ve výchozím editoru nebo omezit na vlastní editor.  
  
 Chcete-li přiřadit klávesové zkratky existujícím položkám nabídky sady Visual Studio, přečtěte si téma [identifikace a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Výběr kombinace kláves  
 V aplikaci Visual Studio se již používá mnoho klávesových zkratek. Neměli byste přiřadit stejný zástupce více než jednomu příkazu, protože duplicitní vazby je obtížné detekovat a mohou také způsobovat nepředvídatelné výsledky. Proto je vhodné před přiřazením ověřit dostupnost zástupce.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Ověření dostupnosti klávesové zkratky  
  
1. V okně **Nástroje/možnosti/prostředí** vyberte **klávesnice**.  
  
2. Ujistěte se, že je **Nový zástupce v** sadě nastavený na **globální**.  
  
3. V poli **klávesových zkratek klávesových zkratek** zadejte klávesovou zkratku, kterou chcete použít.  
  
    Pokud je zástupce již použit v aplikaci Visual Studio, **zástupce aktuálně používaný** v poli zobrazí příkaz, který zástupce aktuálně volá.  
  
4. Vyzkoušejte různé kombinace klíčů, dokud nezjistíte, která z nich není namapovaná.  
  
   > [!NOTE]
   > Klávesové zkratky, které používají ALT, můžou otevřít nabídku a ne přímo spustit příkaz. Proto může být **zástupce aktuálně používaný v** boxu při psaní zástupce, který obsahuje ALT, prázdný. Můžete ověřit, že zástupce neotevře nabídku zavřením dialogového okna **Možnosti** a následným stisknutím kláves.  
  
   Následující postup předpokládá, že máte existující VSPackage s příkazem nabídky. Pokud k tomu potřebujete pomoc, podívejte se na [Vytvoření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Přiřazení klávesové zkratky k příkazu  
  
1. Otevřete soubor. vsct pro váš balíček.  
  
2. Až se v případě, že ještě neexistuje, vytvořte prázdný `<KeyBindings>` oddíl `<Commands>` .  
  
   > [!WARNING]
   > Další informace o vazbách klíčů naleznete v tématu [Binding](../extensibility/keybinding-element.md).  
  
    V `<KeyBindings>` části vytvořte `<KeyBinding>` položku.  
  
    Nastavte `guid`  atributy a  `id` pro příkazy, které chcete vyvolat.  
  
    Nastavte `mod1` atribut na **Control**, **ALT**nebo **SHIFT**.  
  
    Oddíl vazeb klíčů by měl vypadat přibližně takto:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Pokud vaše klávesová zkratka vyžaduje více než dva klíče, nastavte `mod2` `key2` atributy a.  
  
   Ve většině případů by se **SHIFT** neměl používat bez druhého modifikátoru, protože jeho stisknutí má za následek, že většina alfanumerických klíčů zapíše velké písmeno nebo symbol.  
  
   Kódy virtuálních klíčů umožňují přístup ke speciálním klíčům, ke kterým není přiřazen znak, například klávesy funkcí a klávesa **BACKSPACE** . Další informace najdete v tématu [kódy virtuálních klíčů](https://msdn2.microsoft.com/library/ms645540.aspx).  
  
   Chcete-li příkaz zpřístupnit v editoru sady Visual Studio, nastavte `editor` atribut na hodnotu `guidVSStd97` .  
  
   Chcete-li, aby byl příkaz dostupný pouze ve vlastním editoru, nastavte `editor` atribut na název vlastního editoru vygenerovaného [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] šablonou balíčku při vytvoření VSPackage, který obsahuje vlastní editor. Chcete-li zjistit hodnotu názvu, podívejte se do `<Symbols>` části `<GuidSymbol>` uzlu, jehož `name` atribut končí znakem " `editorfactory` .". Toto je název vlastního editoru.  
  
## <a name="example"></a>Příklad  
 Tento příklad váže klávesovou zkratku CTRL + ALT + C k příkazu s názvem `cmdidMyCommand` v balíčku s názvem `MyPackage` .  
  
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
 Tento příklad váže seznam CTL klávesových zkratek + B k příkazu pojmenovanému `cmdidBold` v projektu s názvem `TestEditor` . Příkaz je k dispozici pouze ve vlastním editoru, nikoli v jiných editorech.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Viz také  
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)
