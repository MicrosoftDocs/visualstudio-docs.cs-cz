---
title: Konstanty IDE | Microsoft Docs
description: Třída VSConstants poskytuje konstanty specifické pro integrované vývojové prostředí (IDE), které byly dříve definovány pouze v hlavičkových souborech.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28b419981e8fe1224cef5c25e112d58924a8301b
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995561"
---
# <a name="ide-constants"></a>Konstanty rozhraní IDE

<xref:Microsoft.VisualStudio.VSConstants>Třída poskytuje konstanty, které jsou specifické pro integrované vývojové prostředí (IDE) a které byly dříve definovány pouze v hlavičkových souborech.

## <a name="logical-and-physical-views"></a>Logická a fyzická zobrazení

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny by měly předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodě pro otevření dialogového okna **otevřít** v, v tomto případě u možných zobrazení kódu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny předají tuto hodnotu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody pro získání dialogového okna **otevřít** v, v tomto případě naplněná možnými <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> zobrazeními ladění, která se mapují na stejné zobrazení jako <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny předají tuto hodnotu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody pro získání dialogového okna **otevřít** v, v tomto případě pro zobrazení zobrazení návrháře **formuláře** .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny tuto hodnotu předá <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodě pro získání dialogového okna **otevřít** v, v tomto případě jako výchozí/primární zobrazení objektu pro vytváření editoru.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny předají tuto hodnotu do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody pro získání dialogového okna **otevřít** v, v tomto pro zobrazení dokumentu nebo textového editoru dat.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith`obslužné rutiny předají tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodě, která vyzve uživatele, aby zvolili, které uživatelem definované zobrazení se má použít.|

## <a name="editor-factory-flags"></a>Editor – příznaky objektu factory

|Hodnota|Popis|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Zastaralý příznak kombinovaná bitová kopie jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Kombinovaná bitová kopie jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, to znamená, že objekt pro vytváření editoru by měl provést nezbytné opravy.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|V kombinaci bitové jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody je tento příznak vzájemně nevýlučně [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Tich](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Kombinovaná bitová kopie jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, to znamená, že objekt pro vytváření editoru by měl vytvořit editor bez zobrazení uživatelského rozhraní (UI).|

## <a name="visual-studio-errors"></a>Chyby sady Visual Studio

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Konstanta vrácená rozhraními na asynchronní chování v případě, že je objekt v dotazu již zaneprázdněn|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Chyba HRESULT, která je specifická pro aplikaci Visual Studio pro "nekompatibilní data dokumentu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Došlo k chybě HRESULT, která je specifická pro sadu Visual Studio a která indikuje "balíček není načtený."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Chyba HRESULT, která je specifická pro aplikaci Visual Studio a která indikuje, že projekt již existuje.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Došlo k chybě HRESULT, která je specifická pro aplikaci Visual Studio a která indikuje "konfigurace projektu se nezdařila".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Došlo k chybě HRESULT, která je specifická pro Visual Studio a která indikuje "projekt není načtený".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Došlo k chybě HRESULT, která je specifická pro Visual Studio a indikuje "řešení už je otevřené."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Chyba HRESULT, která je specifická pro Visual Studio a indikuje "řešení není otevřené."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Vráceno rozhraními sestavení, která mají parametry pro zadání pole z <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> rozhraní, ale implementace může použít pouze metodu pro všechny výstupy.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>Metoda vrátí tuto hodnotu, pokud má dokument formát, který nelze otevřít v editoru.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Hodnota HRESULT, která indikuje, že uživatel v průvodci pro Visual Studio narazí na tlačítko zpět.|

## <a name="visual-studio-constants"></a>Konstanty sady Visual Studio

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Došlo k chybě HRESULT, která je specifická pro Visual Studio a která indikuje "předaný projekt."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Konstanta, která je specifická pro sadu Visual Studio pro "značku panelu nástrojů".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Konstanta, která je specifická pro sadu Visual Studio pro vysílání zprávy oznámení přes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodu, která označuje začátek modálníku.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Konstanta, která je specifická pro sadu Visual Studio pro vysílání zprávy oznámení přes <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodu, která označuje konec modálníku.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Konstanta, která je specifická pro Visual Studio pro vysílání zprávy oznámení prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metody indikující, že se změnily metriky panelu příkazů.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Konstanta, která je specifická pro sadu Visual Studio, která indikuje, že soubor cookie nebyl nastaven.|
|[VSITEMID. Nula](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identifikátor položky sady Visual Studio, který představuje absenci položky projektu. Tato hodnota se používá v případě, že není k dispozici žádný aktuální výběr.|
|[VSITEMID. Zobrazuje](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identifikátor položky sady Visual Studio, který představuje kořen hierarchie projektu a slouží k identifikaci celé hierarchie na rozdíl od jedné položky.|
|[VSITEMID. Výběru](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identifikátor položky sady Visual Studio, který představuje aktuálně vybranou položku nebo položky, která může obsahovat kořen hierarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Popisuje, kterou součást rozhraní IDE jste právě vybrali, ve volání například <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> .

|Konstanta|Hodnota|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Konstanty používané k označení nového stavu výběru.

|Konstanta|Hodnota|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Konstanty dialogu pro výběr komponent

|Konstanta|Hodnota|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Viz také

- [Příkazy definované rozhraním IDE pro rozšíření systémů projektů](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
