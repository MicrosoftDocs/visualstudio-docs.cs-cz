---
title: 'Postupy: úprava příkazu standardní nabídky v jazyka specifického pro doménu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .vsct files, adding commands to a domain-specific language
- Domain-Specific Language, adding custom commands
ms.assetid: 9b9d8314-d0d8-421a-acb9-d7e91e69825c
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 3d29a501ef6f55c835efd68e474bc39a847f745d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837557"
---
# <a name="how-to-modify-a-standard-menu-command-in-a-domain-specific-language"></a>Postupy: Úprava příkazu standardní nabídky v jazyce specifickém pro doménu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit chování některé standardní příkazy, které jsou automaticky definována v vašeho DSL. Například můžete změnit **Vyjmout** tak, aby vyloučí citlivé informace. K tomuto účelu přepsání metody ve třídě příkaz set. Tyto třídy jsou definovány v souboru CommandSet.cs v projektu DslPackage a jsou odvozeny z <xref:Microsoft.VisualStudio.Modeling.Shell.CommandSet>.  
  
 Stručně řečeno, úprava příkazu:  
  
1. [Zjistit, jaké příkazy lze upravit](#what).  
  
2. [Vytvořit deklaraci částečné třídy příslušný příkaz set](#extend).  
  
3. [Přepsání metody ProcessOnStatus a ProcessOnMenu](#override) pro příkaz.  
  
   Toto téma vysvětluje postup.  
  
> [!NOTE]
>  Pokud chcete vytvořit vlastní příkazy nabídek, přečtěte si téma [postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
##  <a name="what"></a> Jaké příkazy lze upravit?  
  
#### <a name="to-discover-what-commands-you-can-modify"></a>Pokud chcete zjistit, jaké příkazy, které můžete upravit  
  
1.  V `DslPackage` projekt, otevřete `GeneratedCode\CommandSet.cs`. Tento soubor jazyka C# najdete v okně Průzkumník řešení jako pobočka `CommandSet.tt`.  
  
2.  Hledání třídy v tomto souboru, jejichž názvy končí "`CommandSet`", například `Language1CommandSet` a `Language1ClipboardCommandSet`.  
  
3.  Každá třída set příkazu, zadejte "`override`" následované mezerou. Technologie IntelliSense zobrazí seznam metod, které můžete přepsat. Každý příkaz nemá dvojici metod, jejichž názvy začínají "`ProcessOnStatus`"a"`ProcessOnMenu`".  
  
4.  Poznačte si příkazu nastavit třídy obsahuje příkaz, který chcete upravit.  
  
5.  Zavřete soubor bez uložení úprav.  
  
    > [!NOTE]
    >  Obvykle byste neměli upravovat soubory, které byly vytvořeny. Veškeré úpravy budou ztraceny při příštím tyto soubory jsou vygenerovány.  
  
##  <a name="extend"></a> Rozšíření příslušný příkaz set – třída  
 Vytvořte nový soubor, který obsahuje částečné deklarace třídy příkazu set.  
  
#### <a name="to-extend-the-command-set-class"></a>K rozšíření příkazu Set – třída  
  
1.  V Průzkumníku řešení v projektu DslPackage otevřete složku GeneratedCode a podívejte se do části CommandSet.tt a otevřete její vygenerovaný soubor CommandSet.cs. Poznámka: obor názvů a název první třídy, která je definována existuje. Například může se zobrazit:  
  
     `namespace Company.Language1`  
  
     `{ ...  internal partial class Language1CommandSet : ...`  
  
2.  V **DslPackage**, vytvořte složku s názvem **vlastní kód**. V této složce, vytvořte nový soubor třídy `CommandSet.cs`.  
  
3.  V novém souboru zápisu částečná deklarace, který má stejný obor názvů a název jako vygenerovanou dílčí třídu. Příklad:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.ComponentModel.Design;  
    namespace Company.Language1 /* Make sure this is correct */  
    { internal partial class Language1CommandSet { ...  
    ```  
  
     **Poznámka:** Pokud jste použili k vytvoření nového souboru. soubor šablony třídy, je nutné opravit obor názvů a název třídy.  
  
##  <a name="override"></a> Přepište metody příkaz  
 Většina příkazů mít přidružené dvě metody: metodu s názvem, jako jsou `ProcessOnStatus`... Určuje, zda má být příkaz viditelný a povolený. Je volána, když uživatel klepne pravým tlačítkem myši diagram a by měl rychle spustit a neprovádějte žádné změny. `ProcessOnMenu`... se volá, když uživatel klepne na příkaz a by měl provádět funkce příkazu. Můžete chtít přepsat jeden nebo oba z těchto metod.  
  
### <a name="to-change-when-the-command-appears-on-a-menu"></a>Chcete-li změnit při příkazu se zobrazí v nabídce  
 Přepsat ProcessOnStatus... metody. Tato metoda by měla nastavit viditelné a povolené vlastnosti parametru nabídka – příkaz. Obvykle příkaz vypadá na to. CurrentSelection k určení, zda příkaz se vztahuje na vybrané elementy a se také podívat na jejich vlastnosti k určení, zda příkaz lze použít v jeho aktuálním stavu.  
  
 Jako obecné vodítko byste měli určit vlastnost Visible, ve které prvky jsou vybrány. Vlastnost Enabled, která určuje, zda příkaz bude zdánlivě černou nebo šedá v nabídce, by měl záviset na aktuální stav výběru.  
  
 Následující příklad zakazuje odstranění položky nabídky, když uživatel vybral více než jeden tvar.  
  
> [!NOTE]
>  Tato metoda nemá vliv, zda příkaz je k dispozici prostřednictvím jedním stisknutím tlačítka. Například zakázání odstranění položky nabídky nezabraňuje příkaz vyvolání pomocí klávesu Delete.  
  
```  
/// <summary>  
/// Called when user right-clicks on the diagram or clicks the Edit menu.  
/// </summary>  
/// <param name="command">Set Visible and Enabled properties.</param>  
protected override void ProcessOnStatusDeleteCommand (MenuCommand command)  
{  
  // Default settings from the base method.  
  base.ProcessOnStatusDeleteCommand(command);  
  if (this.CurrentSelection.Count > 1)  
  {  
    // If user has selected more than one item, Delete is greyed out.  
    command.Enabled = false;  
  }  
}  
```  
  
 Je dobrým zvykem nejprve volat základní metodu, všechny případy a nastavení, se kterými jste nejsou obeznámeni.  
  
 Metoda ProcessOnStatus by neměl vytvořit, odstranit nebo aktualizovat prvky Store.  
  
### <a name="to-change-the-behavior-of-the-command"></a>Chcete-li změnit chování příkazu  
 Přepsat ProcessOnMenu... metody. Následující příklad znemožní uživateli odstranění více než jeden prvek v době, dokonce i pomocí klávesu Delete.  
  
```  
/// <summary>  
/// Called when user presses Delete key   
/// or clicks the Delete command on a menu.  
/// </summary>  
protected override void ProcessOnMenuDeleteCommand()  
{  
  // Allow users to delete only one thing at a time.  
  if (this.CurrentSelection.Count <= 1)  
  {  
    base.ProcessOnMenuDeleteCommand();  
  }  
}  
```  
  
 Pokud váš kód provede změny Store, jako je například vytvoření, odstranění nebo aktualizaci elementy nebo propojení, musíte tak učinit v transakci. Další informace najdete v tématu [postupy vytváření a aktualizace prvky modelu](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md).  
  
### <a name="writing-the-code-of-the-methods"></a>Psaní kódu metod  
 Následující fragmenty jsou často užitečné v rámci těchto metod:  
  
- `this.CurrentSelection`. Obrazec, který klikli pravým tlačítkem myši uživatele je vždy součástí tohoto seznamu obrazců a konektorů. Pokud uživatel klikne na prázdnou část diagramu, diagramu je jediným členem seznamu.  
  
- `this.IsDiagramSelected()` - `true` Pokud uživatel klikne na prázdnou část diagramu.  
  
- `this.IsCurrentDiagramEmpty()`  
  
- `this.IsSingleSelection()` -uživatel nevybrali více tvarů  
  
- `this.SingleSelection` – vybraný tvar nebo diagram, který klikli pravým tlačítkem myši uživatele  
  
- `shape.ModelElement as MyLanguageElement` -prvku modelu reprezentovány ve tvaru.  
  
  Další informace o tom, jak přejít z elementu a o tom, jak vytvořit objekty a propojení najdete v tématu [navigace a aktualizace modelu v programovém kódu](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.Design.MenuCommand>   
 [Psaní kódu pro úpravu jazyka specifického pro doménu specifického](../modeling/writing-code-to-customise-a-domain-specific-language.md)   
 [Postupy: přidání příkazu do místní nabídky](../modeling/how-to-add-a-command-to-the-shortcut-menu.md)   
 [Postupy: Získávání informací z vybraného odkazu](../misc/walkthrough-getting-information-from-a-selected-link.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Tabulky příkazů sady Visual Studio (. Soubory Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Referenční dokumentace schématu VSCT XML](../extensibility/vsct-xml-schema-reference.md)   
 [Vmsdk následující položky – ukázka okruhů. Přizpůsobení rozsáhlé DSL](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)   
 [Ukázkový kód: diagramy okruh](http://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)



