---
title: Zpřístupnění příkazů | Dokumenty společnosti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707325"
---
# <a name="making-commands-available"></a>Zpřístupnění příkazů

Při přidání více VSPackages do sady Visual Studio, uživatelské rozhraní (UI) může být přeplněný s příkazy. Balíček můžete naprogramovat tak, aby tento problém pomohl snížit, a to následujícím způsobem:

- Naprogramujte balíček tak, aby byl načten pouze v případě, že jej uživatel vyžaduje.

- Naprogramujte balíček tak, aby jeho příkazy byly zobrazeny pouze v případě, že mohou být požadovány v kontextu aktuálního stavu integrovaného vývojového prostředí (IDE).

## <a name="delayed-loading"></a>Zpožděné načítání

Typický způsob, jak povolit zpožděné načítání je navrhnout VSPackage tak, aby jeho příkazy jsou zobrazeny v uživatelském rozhraní, ale samotný balíček není načten, dokud uživatel klepne na jeden z příkazů. Chcete-li to provést, vytvořte v souboru .vsct příkazy, které nemají žádné příznaky příkazů.

Následující příklad ukazuje definici příkazu nabídky ze souboru .vsct. Toto je příkaz, který je generován šablonou balíčku sady Visual Studio, když je vybrána možnost **Příkaz nabídky** v šabloně.

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

V příkladu, pokud nadřazená skupina , je podřízená nabídce nejvyšší úrovně, například v nabídce `MyMenuGroup` **Nástroje,** bude příkaz viditelný v této nabídce, ale balíček, který provede příkaz, nebude načten, dokud uživatel neklepne na příkaz. Programováním příkazu k implementaci <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní však můžete povolit načtení balíčku při prvním rozbalení nabídky obsahující příkaz.

Všimněte si, že zpožděné načítání může také zlepšit výkon při spuštění.

## <a name="current-context-and-the-visibility-of-commands"></a>Aktuální kontext a viditelnost příkazů

Příkazy VSPackage můžete naprogramovat tak, aby byly viditelné nebo skryté, v závislosti na aktuálním stavu dat VSPackage nebo na akcích, které jsou aktuálně relevantní. Můžete povolit VSPackage nastavit stav jeho příkazy, obvykle pomocí implementace <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A> metody <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> z rozhraní, ale to vyžaduje VSPackage načíst před spuštěním kódu. Místo toho doporučujeme povolit ide pro správu viditelnosti příkazů bez načtení balíčku. Chcete-li to provést, v souboru .vsct přidružte příkazy k jednomu nebo více speciálním kontextům ui. Tyto kontexty uživatelského rozhraní jsou identifikovány identifikátorem GUID označovanou jako *identifikátor GUID kontextu příkazu*.

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]monitoruje změny, které jsou výsledkem akcí uživatelů, jako je například načtení projektu nebo přecházení z úprav do budovy. Jak dochází ke změnám, vzhled ide se automaticky změní. V následující tabulce jsou uvedeny čtyři [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hlavní kontexty změny ide, které monitoruje.

| Typ kontextu | Popis |
|-------------------------| - |
| Aktivní typ projektu | Pro většinu typů `GUID` projektu je tato hodnota stejná jako identifikátor GUID balíčku VSPackage, který implementuje projekt. Projekty [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] však použít `GUID` typ projektu jako hodnotu. |
| Aktivní okno | Obvykle se jedná o poslední aktivní okno dokumentu, které vytváří aktuální kontext ui pro vazby klíčů. Může se však také jedná o okno nástroje, které má tabulku vazby klíčů, která se podobá internímu webovému prohlížeči. U oken dokumentů s více kartami, například v editoru HTML, má každá karta jiný kontext `GUID`příkazů . |
| Služba aktivního jazyka | Jazyková služba přidružená k souboru, který je aktuálně zobrazen v textovém editoru. |
| Okno aktivního nástroje | Okno nástroje, které je otevřené a má fokus. |

Pátá hlavní kontextová oblast je stav ui ide. Kontexty ui jsou identifikovány `GUID`podle kontextu aktivního příkazu s takto:

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

Tyto identifikátory GUID jsou označeny jako aktivní nebo neaktivní, v závislosti na aktuálním stavu rozhraní IDE. Více kontextů ui může být aktivní současně.

### <a name="hide-and-display-commands-based-on-context"></a>Skrytí a zobrazení příkazů na základě kontextu

Příkaz balíčku můžete zobrazit nebo skrýt v ide bez načtení samotného balíčku. Chcete-li to provést, definujte příkaz v `DefaultDisabled`souboru .vsct balíčku pomocí příznaků , `DefaultInvisible`a příkaz `DynamicVisibility` a přidejte jeden nebo více prvků [VisibilityItem](../../extensibility/visibilityitem-element.md) do oddílu [VisibilityConstraints.](../../extensibility/visibilityconstraints-element.md) Když se zadaný kontext `GUID` příkazu stane aktivním, příkaz se zobrazí bez načtení balíčku.

### <a name="custom-context-guids"></a>Vlastní identifikátory GUID kontextu

Pokud není ještě definován identifikátor GUID kontextu příslušného příkazu, můžete jej definovat v balíčku VSPackage a poté jej naprogramovat tak, aby byl aktivní nebo neaktivní, jak je požadováno pro řízení viditelnosti příkazů. Službu <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> použijte k:

- Zaregistrujte identifikátory GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCmdUIContextCookie%2A> kontextu (voláním metody).

- Získat stav kontextu `GUID` (voláním <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> metody).

- Zapněte `GUID`a vypněte kontext s <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.SetCmdUIContext%2A> (voláním metody).

    > [!CAUTION]
    > Ujistěte se, že váš VSPackage nemá vliv na stav existující ho kontextu GUID, protože ostatní VSPackages může záviset na nich.

## <a name="example"></a>Příklad

Následující příklad příkazu VSPackage ukazuje dynamickou viditelnost příkazu, který je spravován kontexty příkazů bez načtení vbalíčku VSPackage.

Příkaz je nastaven tak, aby byl povolen a zobrazen vždy, když existuje řešení; to znamená, že vždy, když je aktivní jeden z následujících identifikátorů GUID kontextu příkazu:

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.EmptySolution_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasMultipleProjects_guid>

- <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionHasSingleProject_guid>

V příkladu všimněte si, že každý příkaz ový příznak je samostatný prvek [command flag.](../../extensibility/command-flag-element.md)

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

Všimněte si také, že každý kontext `VisibilityItem` ui musí být uveden v samostatném prvku, takto.

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

- [Přidání příkazu na panel nástrojů Průzkumníka řešení](../../extensibility/adding-a-command-to-the-solution-explorer-toolbar.md)
- [Jak balíčky VSPackages přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Směrování příkazů v balíčcích VSPackage](../../extensibility/internals/command-routing-in-vspackages.md)
- [Dynamické přidávání položek nabídky](../../extensibility/dynamically-adding-menu-items.md)
