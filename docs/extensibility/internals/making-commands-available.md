---
title: Zpřístupnění příkazů | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- menus [Visual Studio SDK], commands
- best practices, menu and toolbar commands
- toolbars [Visual Studio], best practices
- menu commands, best practices
ms.assetid: 3ffc4312-c6db-4759-a946-a4bb85f4a17a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d64df85516e0a1ac326f8d40558755718c4644c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707325"
---
# <a name="making-commands-available"></a>Zpřístupnění příkazů

Při přidání více rozhraní VSPackage do sady Visual Studio může být uživatelské rozhraní (UI) přeplněno příkazy. Pomocí následujícího postupu můžete naprogramovat balíček, který vám pomůže tento problém snížit:

- Naprogramujte balíček tak, aby se načetl jenom v případě, že ho uživatel potřebuje.

- Naprogramujte balíček tak, aby se jeho příkazy zobrazovaly jenom v případě, že se můžou vyžadovat v kontextu aktuálního stavu integrovaného vývojového prostředí (IDE).

## <a name="delayed-loading"></a>Zpožděné načítání

Typický způsob, jak povolit zpožděné načítání, je navrhnout rozhraní VSPackage tak, aby se jeho příkazy zobrazovaly v uživatelském rozhraní, ale samotný balíček se nenačte, dokud uživatel neklikne na jeden z příkazů. Chcete-li to provést, vytvořte v souboru. vsct příkazy, které nemají žádné příznaky příkazu.

Následující příklad ukazuje definici příkazu nabídky ze souboru. vsct. Toto je příkaz, který je generován šablonou balíčku sady Visual Studio při výběru možnosti **příkazu nabídky** v šabloně.

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

V případě, že je nadřazená skupina `MyMenuGroup` Podřízená nabídce nejvyšší úrovně, jako je například nabídka **nástroje** , příkaz bude v této nabídce viditelný, ale balíček, který příkaz spustí, nebude načten, dokud na něj neklikne uživatel. Nicméně programováním příkazu pro implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní můžete povolit načtení balíčku při prvním rozšíření nabídky, která obsahuje příkaz.

Všimněte si, že zpožděné načítání může také zlepšit výkon při spuštění.

## <a name="current-context-and-the-visibility-of-commands"></a>Aktuální kontext a viditelnost příkazů

Můžete programovat příkazy VSPackage, aby byly viditelné nebo skryté v závislosti na aktuálním stavu dat VSPackage nebo akcí, které jsou aktuálně relevantní. Můžete povolit, aby VSPackage nastavil stav svých příkazů, obvykle pomocí implementace <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody z <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní, ale to vyžaduje, aby rozhraní VSPackage bylo načteno před tím, než může spustit kód. Místo toho doporučujeme povolit integrované vývojové prostředí (IDE) pro správu viditelnosti příkazů bez načtení balíčku. Chcete-li to provést, v souboru. vsct přidružte příkazy k jednomu nebo více speciálních kontextům uživatelského rozhraní. Tyto kontexty uživatelského rozhraní jsou označeny identifikátorem GUID, který je známý jako *identifikátor GUID kontextu příkazu*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitoruje změny, které jsou výsledkem akcí uživatele, jako je například načítání projektu nebo úpravy při sestavování. Když dojde ke změnám, vzhled IDE se automaticky upraví. V následující tabulce jsou uvedeny čtyři hlavní kontexty pro změnu IDE, které [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] monitorují.

| Typ kontextu | Popis |
|-------------------------| - |
| Typ aktivního projektu | Pro většinu typů projektů je tato `GUID` hodnota shodná s identifikátorem GUID VSPackage, který implementuje projekt. Projekty však [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] jako hodnotu používají typ projektu `GUID` . |
| Aktivní okno | Obvykle se jedná o poslední okno aktivního dokumentu, které vytváří aktuální kontext uživatelského rozhraní pro klíčové vazby. Může to být také okno nástroje, které má tabulku vazby klíčů, která se podobá internímu webovému prohlížeči. U oken dokumentů s více kartami, jako je editor HTML, má každá karta jiný kontext příkazů `GUID` . |
| Služba Active Language | Služba jazyka, která je přidružena k souboru, který je aktuálně zobrazen v textovém editoru. |
| Aktivní okno nástrojů | Okno nástroje, které je otevřeno a má fokus. |

Pátá hlavní kontextová oblast je stav uživatelského rozhraní rozhraní IDE. Kontexty uživatelského rozhraní jsou identifikovány pomocí kontextu aktivního příkazu `GUID` s následujícím způsobem:

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

Tyto identifikátory GUID jsou označeny jako aktivní nebo neaktivní v závislosti na aktuálním stavu rozhraní IDE. Současně může být aktivní více kontextů uživatelského rozhraní.

### <a name="hide-and-display-commands-based-on-context"></a>Skrýt a zobrazit příkazy založené na kontextu

V integrovaném vývojovém prostředí můžete zobrazit nebo skrýt příkaz balíčku bez načtení samotného balíčku. Chcete-li to provést, definujte příkaz v souboru. vsct balíčku pomocí `DefaultDisabled` `DefaultInvisible` `DynamicVisibility` příznaků příkazu, a a přidejte jeden nebo více [VisibilityItem](../../extensibility/visibilityitem-element.md) prvků do oddílu [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) . Když je zadaný kontext příkazu `GUID` aktivní, příkaz se zobrazí bez načtení balíčku.

### <a name="custom-context-guids"></a>Identifikátory GUID vlastního kontextu

Pokud identifikátor GUID příslušného kontextu příkazu ještě není definovaný, můžete ho definovat ve VSPackage a pak ho programovat jako aktivní nebo neaktivní, jak je potřeba k řízení viditelnosti příkazů. Použijte <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> službu pro:

- Registrovat identifikátory GUID kontextu (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> metody).

- Získání stavu kontextu `GUID` (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody).

- Zapnout `GUID` a vypnout kontext s (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> metody).

    > [!CAUTION]
    > Ujistěte se, že VSPackage nemá vliv na stav žádného stávajícího identifikátoru GUID kontextu, protože na nich mohou být závislé jiné sady VSPackage.

## <a name="example"></a>Příklad

Následující příklad příkazu VSPackage ukazuje dynamickou viditelnost příkazu, který je spravován kontexty příkazů bez načtení VSPackage.

Příkaz je nastaven tak, aby byl povolen a zobrazen vždy, když existuje řešení; To znamená, že pokud je aktivní jeden z následujících identifikátorů GUID kontextu příkazu:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

V příkladu si všimněte, že každý příznak příkazu je samostatný prvek [příznaku příkazu](../../extensibility/command-flag-element.md) .

```xml
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

Všimněte si také, že každý kontext uživatelského rozhraní musí být uveden v samostatném `VisibilityItem` prvku následujícím způsobem.

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

- [Přidání příkazu na panel nástrojů Průzkumník řešení](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamické přidávání položek nabídky](../../extensibility/dynamically-adding-menu-items.md)
