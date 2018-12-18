---
title: Vazba klávesové zkratky a položkami nabídky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66436f31a0c2f3b895b4f12a5fb352eddf685632
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219637"
---
# <a name="bind-keyboard-shortcuts-to-menu-items"></a>Vytvoření vazby klávesové zkratky a položkami nabídky
K vytvoření vazby příkazu nabídky vlastní klávesové zkratky, stačí přidat položku *.vsct* souborů pro balíček. Toto téma vysvětluje, jak namapovat na vlastní tlačítka, položka nabídky nebo panelu nástrojů příkazu Klávesové zkratky a použít mapování klávesnice v editoru výchozí nebo omezit na vlastní editor.  
  
 Přiřazení klávesových zkratek pro existující položky nabídky sady Visual Studio, naleznete v tématu [identifikovat a přizpůsobení klávesových zkratek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choose-a-key-combination"></a>Zvolte kombinaci klíče  
 Mnoho klávesové zkratky se už používají v sadě Visual Studio. Stejnou klávesovou zkratku by neměl přiřadit více než jeden příkaz, protože duplicitní vazby je obtížné rozpoznat a může také vést k nepředvídatelným výsledkům. Proto je vhodné ověřit dostupnost zástupce, před jeho přiřazením.  
  
### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Chcete-li ověřit dostupnost klávesové zkratky  
  
1. V **nástroje** > **možnosti** > **prostředí** okně **klávesnice**.  
  
2. Ujistěte se, že **použití nového zástupce v:** je nastavena na **globální**.  
  
3. V **stiskněte klávesovou zkratku** zadejte klávesovou zkratku, kterou chcete použít.  
  
    Pokud zástupce se už používá v sadě Visual Studio **zkratku aktuálně používá** poli se zobrazí příkaz, který aktuálně volá klávesovou zkratku.  
  
4. Zkuste různé kombinace kláves, dokud nenaleznete, která není namapována.  
  
   > [!NOTE]
   >  Klávesové zkratky, které používají **Alt** může otevřít nabídku a ne přímo provedení příkazu. Proto **zkratku aktuálně používá** pole nesmí být prázdný, když zadáte zástupce, který zahrnuje **Alt**. Můžete ověřit, že zástupce není otevřete nabídku podle uzavírací **možnosti** dialogové okno a potom stisknutím kláves.  
  
   Následující postup předpokládá, že máte existující balíčku VSPackage pomocí příkazu nabídky. Pokud potřebujete pomoc, to provedete, podívejte se na [vytváření rozšíření pomocí příkazu nabídky](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Chcete-li přiřadit klávesovou zkratku k příkazu  
  
1. Otevřít *.vsct* souboru balíčku.  
  
2. Vytvořte prázdnou `<KeyBindings>` části po `<Commands>` Pokud ještě není k dispozici.  
  
   > [!WARNING]
   >  Další informace o klávesové zkratky, naleznete v tématu [klávesové zkratky](../extensibility/keybinding-element.md).  
  
    V `<KeyBindings>` části, vytvořte `<KeyBinding>` položka.  
  
    Nastavte `guid` a `id` atributy u těch, které chcete vyvolat příkaz.  
  
    Nastavte `mod1` atribut **ovládací prvek**, **Alt**, nebo **Shift**.  
  
    Klávesové zkratky oddíl by měl vypadat přibližně takto:  
  
   ```xml  
   <KeyBindings>  
       <KeyBinding guid="<name of command set>" id="<name of command id>"  
           editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
   </KeyBindings>  
  
   ```  
  
   Pokud je klávesová zkratka vyžaduje více než dva klíče, nastavte `mod2` a `key2` atributy.  
  
   Ve většině případů **Shift** by neměl bez druhý modifikátor použít, protože již stisknutím klávesy způsobí, že většina alfanumerické klíčů na typ symbolu nebo velké písmeno.  
  
   Virtuální klíč kódy umožňují přístup ke speciální klávesy, které nemají znak spojený s nimi, například funkční klávesy a **Backspace** klíč. Další informace najdete v tématu [virtuální klíč kódy](https://docs.microsoft.com/windows/desktop/inputdev/virtual-key-codes).  
  
   Chcete-li příkaz k dispozici v sadě Visual Studio editoru, nastavte `editor` atribut `guidVSStd97`.  
  
   Chcete-li příkaz k dispozici pouze ve vlastním editoru, nastavte `editor` atribut název vlastní editor, který byl vytvořen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] balíček šablony při vytváření sady VSPackage, která obsahuje vlastní editor. Chcete-li najít hodnoty názvu, podívejte `<Symbols>` v části `<GuidSymbol>` uzel jehož `name` atribut končí na "`editorfactory`." Toto je název vlastního editoru.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří vazbu klávesové zkratky **Ctrl**+**Alt**+**C** k příkazu s názvem `cmdidMyCommand` v balíčku s názvem `MyPackage`.  
  
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
 Tento příklad vytvoří vazbu klávesové zkratky **Ctrl**+**B** k příkazu s názvem `cmdidBold` v projektu s názvem `TestEditor`. Příkaz je k dispozici pouze ve vlastním editoru a ne v jiném editoru.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>Viz také:  
 [Rozšiřování nabídek a příkazů](../extensibility/extending-menus-and-commands.md)