---
title: Konstanty IDE | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710505"
---
# <a name="ide-constants"></a>Konstanty IDE

Třída <xref:Microsoft.VisualStudio.VSConstants> poskytuje konstanty, které jsou specifické pro integrované vývojové prostředí (IDE) a které byly dříve definovány pouze v souborech hlaviček.

## <a name="logical-and-physical-views"></a>Logická a fyzická zobrazení

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> by měl předat tuto hodnotu metodě získat **otevřít v** dialogovém okně, v tomto případě na možných zobrazení kódu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny předat tuto hodnotu metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> získat otevřít <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> **v** dialogovém okně, v tomto <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>případě naplněný možné ladění zobrazení, která mapovat na stejné zobrazení jako .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny předat tuto hodnotu metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> získat otevřít **s** dialogové okno, v tomto případě zobrazit zobrazení návrháře **formuláře.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny předat tuto hodnotu metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> získat otevřít **v** dialogovém okně, v tomto případě výchozí/primární zobrazení editor factory.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny předat tuto hodnotu metodě <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> získat otevřít v **dialogovém** okně, v tomto pro zobrazení textového editoru dokumentu nebo dat.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` obslužné rutiny předat tuto hodnotu metodě, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> která vyzve uživatele k výběru, které uživatelem definované zobrazení použít.|

## <a name="editor-factory-flags"></a>Příznaky továrny editoru

|Hodnota|Popis|
|-----------|-----------------|
|[Cef. Soubor klonování](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Zastaralý příznak v kombinaci bitové jako <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> první parametr metody.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Kombinované bitové jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metoda, to znamená, že editor factory by měl provádět nezbytné opravy.|
|[Cef. Otevřít soubor](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Kombinované bitové jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, tento příznak se vzájemně vylučuje [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Tichý](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Kombinované bitové jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody, to znamená, že editor factory by měl vytvořit editor bez zobrazení uživatelského rozhraní (UI).|

## <a name="visual-studio-errors"></a>Chyby sady Visual Studio

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Konstanta vrácená rozhraními k asynchronnímu chování, když je dotyčný objekt již zaneprázdněn|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Chyba HRESULT, která je specifická pro Visual Studio pro "Nekompatibilní data dokumentu".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Chyba HRESULT, která je specifická pro Visual Studio a která označuje "Balíček není načten."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Chyba HRESULT, která je specifická pro Visual Studio a která označuje, že "Projekt již existuje."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Chyba HRESULT, která je specifická pro Visual Studio a označuje "Konfigurace projektu se nezdařila."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Chyba HRESULT, která je specifická pro Visual Studio a která označuje "Project není načten."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Chyba HRESULT, která je specifická pro Visual Studio a která označuje "Řešení již otevřené."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Chyba HRESULT, která je specifická pro Visual Studio a označuje "Řešení není otevřeno."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Vráceno sestavení rozhraní, které mají parametry pro <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> určení pole z rozhraní, ale implementace lze použít pouze metodu pro všechny výstupy.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Metoda <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> vrátí tuto hodnotu, pokud dokument má formát, který nelze otevřít v editoru.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Hodnota HRESULT, která označuje, že uživatel stiskl tlačítko Zpět v průvodci sady Visual Studio.|

## <a name="visual-studio-constants"></a>Konstanty Visual Studio

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Chyba HRESULT, která je specifická pro Visual Studio a která označuje "Projekt předáno dál."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Konstanta, která je specifická pro Visual Studio pro "Značky panelu nástrojů."|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Konstanta, která je specifická pro Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> pro vysílání oznámení prostřednictvím metody, která označuje začátek modality.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Konstanta, která je specifická pro Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> pro vysílání oznámení prostřednictvím metody, která označuje konec modality.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Konstanta, která je specifická pro Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> pro vysílání oznámení prostřednictvím metody označující, že metriky panelu příkazů byly změněny.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Konstanta, která je specifická pro Visual Studio, která označuje, že soubor cookie nebyl nastaven.|
|[VSITEMID. Nulová hodnota](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identifikátor položky visual studio, který představuje nepřítomnost položky projektu. Tato hodnota se používá, pokud není k dispozici žádný aktuální výběr.|
|[VSITEMID. Kořenové](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identifikátor položky Visual Studio, který představuje kořen hierarchie projektu a slouží k identifikaci celé hierarchie, na rozdíl od jedné položky.|
|[VSITEMID. Výběr](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identifikátor položky sady Visual Studio, který představuje aktuálně vybranou položku nebo položky, které mohou obsahovat kořen hierarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Popisuje, jaká součást ide byla právě vybrána, například <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> volání.

|Trvalé|Hodnota|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.propertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Konstanty používané k označení nového stavu výběru.

|Trvalé|Hodnota|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Konstanty dialogového okna selektoru komponent

|Trvalé|Hodnota|
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

- [Příkazy definované ide pro rozšíření projektových systémů](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
