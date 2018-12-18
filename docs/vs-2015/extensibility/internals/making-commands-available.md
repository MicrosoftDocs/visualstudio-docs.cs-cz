---
title: Zpřístupnění příkazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
caps.latest.revision: 36
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 00ed8231641718b6d0dce8d535b0c43e40b83dd8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783035"
---
# <a name="making-commands-available"></a>Zpřístupnění příkazů
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Při více rozšíření VSPackages přidávají do sady Visual Studio, může být pomocí příkazů přeplněné uživatelského rozhraní (UI). Můžete naprogramovat váš balíček ke zmírnění tohoto problému, následujícím způsobem:  
  
-   Program balíčku tak, aby se načetl pouze v případě, že uživatel vyžaduje.  
  
-   Balíček naprogramovat tak, aby jeho příkazy se zobrazí jenom v případě, že může být nutné v kontextu aktuálního stavu integrovaného vývojového prostředí (IDE).  
  
## <a name="delayed-loading"></a>S odloženým načtením  
 Typické způsob, jak povolit s odloženým načtením je návrh sady VSPackage, aby jeho příkazy jsou zobrazeny v uživatelském rozhraní, ale není načten samotném balíčku, dokud uživatel neklikne jeden z příkazů. Provedete to, že v souboru .vsct vytvořte příkazy, které mají bez příznaků příkazů.  
  
 Následující příklad ukazuje definici příkazu nabídky ze souboru .vsct. Toto je příkaz, který je generován šabloně balíčku Visual Studio při **příkazu nabídky** je vybraná možnost v šabloně.  
  
```xml  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 V příkladu Pokud nadřazené skupiny, `MyMenuGroup`, je podřízeným prvkem nabídek nejvyšší úrovně, jako **nástroje** nabídky, příkaz se nebude zobrazovat v této nabídce, ale balíček, který provede příkaz nebudou načteny, dokud dojde ke kliknutí na příkaz uživatelem. Ale tím, že příkaz k implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, můžete povolit balíček, který má být načten při prvním rozbalení nabídky, která obsahuje příkaz.  
  
 Všimněte si, že opožděné načtení může také zvýšit výkon spuštění.  
  
## <a name="current-context-and-the-visibility-of-commands"></a>Aktuální kontext a viditelnost příkazů  
 Můžete naprogramovat VSPackage příkazy jako viditelný nebo skrytý, v závislosti na aktuální stav dat balíčku VSPackage nebo akce, které jsou aktuálně relevantní. Můžete povolit balíčku VSPackage pro nastavení stavu příkazů, obvykle prostřednictvím implementace <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metodu z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, ale to vyžaduje sady VSPackage, který se má načíst předtím, než se může spustit kód. Namísto toho doporučujeme, abyste povolili integrovaného vývojového prostředí pro správu, zda se příkazy bez načtení balíčku. Provedete to, že v souboru .vsct přidružit jeden nebo více speciálních kontexty uživatelského rozhraní příkazů. Kontexty uživatelského rozhraní jsou označeny identifikátorem GUID říká *kontext příkazů GUID*.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sleduje změny, které jsou výsledkem akce uživatelů, například načítání projektu nebo pokud v úpravách sestavování. Změny se projeví, je automaticky upravit vzhled integrovaného vývojového prostředí. Následující tabulka obsahuje čtyři hlavní kontexty IDE změnit [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] monitorování.  
  
|Typ kontextu|Popis|  
|---------------------|-----------------|  
|Typ aktivní projekt|Pro většinu typů projektu to `GUID` hodnota je stejná jako identifikátor GUID sady VSPackage, která implementuje projektu. Ale [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektů pomocí typu projektu `GUID` jako hodnotu.|  
|Aktivní okno|Obvykle je to poslední aktivního okna dokumentu, který stanoví kontext aktuálního uživatelského rozhraní pro vazby klíčů. Nicméně je možné také panelu nástrojů, která má vazbu klíče tabulku, která vypadá podobně jako interní webový prohlížeč. Pro dokument s kartami s více windows jako je například HTML editor má každá karta jiný příkaz kontextu `GUID`.|  
|Služba Active jazyka|Služba jazyka, který je spojen se souborem, který se nyní zobrazí v textovém editoru.|  
|Aktivní okno nástrojů|Okno nástroje, který je otevřený a má fokus.|  
  
 Na páté hlavní kontextu oblast je stav uživatelského rozhraní IDE. Kontexty uživatelského rozhraní jsou označeny kontextu aktivní příkaz `GUID`s následujícím způsobem:  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionBuilding_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Debugging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.Dragging_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.FullScreenMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.DesignMode_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.NoSolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.CodeWindow_guid>
  
  Tyto GUID identifikátory jsou označeny jako aktivní nebo neaktivní, v závislosti na aktuální stav rozhraní IDE. Kontexty více uživatelského rozhraní může být aktivní ve stejnou dobu.  
  
### <a name="hiding-and-displaying-commands-based-on-context"></a>Skrytí a zobrazení příkazy na základě kontextu  
 Můžete zobrazit nebo skrýt příkaz balíčku v integrovaném vývojovém prostředí bez načtení samotném balíčku. K tomuto účelu definovat příkaz v souboru .vsct balíčku pomocí `DefaultDisabled`, `DefaultInvisible`, a `DynamicVisibility` příkaz příznaky a přidat jeden nebo více [visibilityitem –](../../extensibility/visibilityitem-element.md) prvků, které mají [ Visibilityconstraints –](../../extensibility/visibilityconstraints-element.md) oddílu. Pokud zadaný příkaz kontextu `GUID` stane aktivní, se zobrazí příkaz bez načtení balíčku.  
  
### <a name="custom-context-guids"></a>Vlastní místní GUID  
 Pokud příslušný příkaz kontextu, již není definovaný identifikátor GUID, můžete definovat v vašeho balíčku VSPackage a pak naprogramovat tak být aktivní nebo neaktivní podle potřeby řídit viditelnost příkazů. Použití <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> služby na:  
  
-   Zaregistrovat GUID kontextu (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metoda).  
  
-   Získat informace o stavu kontextu `GUID` (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metoda).  
  
-   Zapnout kontextu `GUID`s zapnout a vypnout (pomocí volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metoda).  
  
    > [!CAUTION]
    >  Ujistěte se, že vaše VSPackage nemá vliv na stav jakýkoli existující kontext GUID vzhledem k tomu, že ostatní rozšíření VSPackages může záviset na ně.  
  
## <a name="example"></a>Příklad  
 Následující příklad příkazu VSPackage ukazuje dynamické viditelnost příkaz, který je spravován kontexty příkaz bez načtení sady VSPackage.  
  
 Příkaz je nastavena na povolena a zobrazí pokaždé, když existuje řešení To znamená vždy, když je jeden z kontextu následující příkaz identifikátory GUID aktivní:  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>  
  
- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>  
  
  V příkladu, Všimněte si, že každý příkaz příznak je samostatný [příkazu příznak](../../extensibility/command-flag-element.md) elementu.  
  
```  
<Button guid="guidDynamicVisibilityCmdSet" id="cmdidMyCommand"   
        priority="0x0100" type="Button">  
  <Parent guid="guidDynamicVisibilityCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <CommandFlag>DefaultDisabled</CommandFlag>  
  <CommandFlag>DefaultInvisible</CommandFlag>  
  <CommandFlag>DynamicVisibility</CommandFlag>  
  <Strings>  
    <CommandName>cmdidMyCommand</CommandName>  
    <ButtonText>My Command name</ButtonText>  
  </Strings>  
</Button>  
  
```  
  
 Také Všimněte si, že každý kontextu uživatelského rozhraní se musí předávat v samostatném `VisibilityItem` element následujícím způsobem.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_EmptySolution" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                      id="cmdidMyCommand" context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidDynamicVisibilityCmdSet"  
                  id="cmdidMyCommand" context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
  
```  
  
## <a name="see-also"></a>Viz také  
 [MenuCommands Vs. OleMenuCommands](../../misc/menucommands-vs-olemenucommands.md)   
 [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Dynamické přidávání položek nabídky](../../extensibility/dynamically-adding-menu-items.md)

