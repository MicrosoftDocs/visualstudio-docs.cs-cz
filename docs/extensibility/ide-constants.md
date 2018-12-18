---
title: Konstanty integrovaného vývojového prostředí | Dokumentace Microsoftu
ms.date: 03/22/2018
ms.technology:
- vs-ide-sdk
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
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4f2cf01bcc8b2854eb1e4c3c711af524a8480bdc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42635129"
---
# <a name="ide-constants"></a>Konstanty integrovaného vývojového prostředí

<xref:Microsoft.VisualStudio.VSConstants> Třída obsahuje konstanty, které jsou specifické pro integrované vývojové prostředí (IDE) a které byly dříve definovány pouze v souborech hlaviček.

## <a name="logical-and-physical-views"></a>Logické a fyzické zobrazení

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny by měla předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k získání **otevřít v** dialogové okno, v tomto případě na zobrazení kódu je to možné.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k získání **otevřít v** dialogové okno, v tomto případě vyplní možné <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> ladění zobrazení, které mapují na stejném zobrazení jako <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k získání **otevřít v** dialogové okno, v tomto případě k **zobrazit formulář** návrháře zobrazení.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k získání **otevřít v** dialogové okno, v tomto případě primární výchozí zobrazení objektu pro vytváření editoru.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu k získání **otevřít v** dialogové okno, v tomto dokumentu nebo data zobrazení editoru textu.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` obslužné rutiny předat tuto hodnotu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodu, která se zobrazí výzva k výběru zobrazení definované uživatelem.|

## <a name="editor-factory-flags"></a>Příznaky Factory editoru

|Hodnota|Popis|
|-----------|-----------------|
|[FORMÁT CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Zastaralé příznak kombinovat bitový jako první parametr <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody.|
|[CEF.OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Bitový operátor jako první parametr v kombinaci <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metoda, znamená to objekt factory editoru by měl provádět potřebné opravy.|
|[CEF.OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Bitový jako první parametr v kombinaci <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metody tohoto příznaku je vzájemně exclusive [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[FORMÁT CEF. Tiché](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Bitový operátor jako první parametr v kombinaci <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metoda, znamená to objekt factory editoru měli vytvořit editoru bez zobrazení uživatelského rozhraní (UI).|

## <a name="visual-studio-errors"></a>Chyb sady Visual Studio

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Konstanta vrácené rozhraní asynchronní chování při v objektu již obsazeno.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Chyba HRESULT, která je specifická pro Visual Studio pro "nekompatibilní dokumentu data".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Chybu HRESULT, která je specifická pro Visual Studio a který určuje "Balíček není načtená."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Chybu HRESULT, která je specifická pro Visual Studio a, která označuje, že "Projekt již existuje."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Chybu HRESULT, která je specifická pro Visual Studio a, která označuje "konfigurace projektu se nezdařilo."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Chybu HRESULT, která je specifická pro Visual Studio a který určuje "Projekt nenačetl."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Označuje chybu HRESULT, která je specifická pro Visual Studio a že "Řešení otevřen."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Chybu HRESULT, která je specifická pro Visual Studio a, která označuje "Řešení není otevřené."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Vrácený rozhraními sestavení, které mají parametry pro určení pole z <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> rozhraní, ale implementace lze použít pouze metodu pro všechny výstupy.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> Metoda vrátí tuto hodnotu, pokud má dokument formátu, který nelze otevřít v editoru.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Hodnota HRESULT, která označuje, že uživatel stiskněte tlačítko Zpět v Průvodci sady Visual Studio.|

## <a name="visual-studio-constants"></a>Visual Studio konstanty

|Hodnota|Popis|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Chybu HRESULT, která je specifická pro Visual Studio a který určuje "Projekt předané."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Konstanta, která je specifická pro Visual Studio pro "panel nástrojů značku."|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Konstanta, která je specifická pro Visual Studio pro všesměrové vysílání zprávy oznámení prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodu, která označuje začátek modalitě.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Konstanta, která je specifická pro Visual Studio pro všesměrové vysílání zprávy oznámení prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodu, která označuje konec modalitě.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Konstanta, která je specifická pro Visual Studio pro všesměrové vysílání zprávy oznámení prostřednictvím <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metoda označující, že došlo ke změně metriky příkazového řádku.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Konstanta, která je specifická pro Visual Studio, která označuje, že soubor cookie není nastavený.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identifikátor položky sady Visual Studio, představujícího chybějící položky projektu. Tato hodnota se používá, pokud nebyla vybrána žádná aktuální položka.|
|[VSITEMID. Kořenové](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identifikátor položky sady Visual Studio, který představuje nejnižší úrovni hierarchie projektu a slouží k identifikaci celou hierarchii, na rozdíl od jedné položky.|
|[VSITEMID. Výběr](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identifikátor položky sady Visual Studio, který představuje aktuálně vybrané položky nebo položek, které mohou zahrnovat kořenu hierarchie.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Popisuje, jaká součást rozhraní IDE jenom byl vybrán, v <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> volat, například.

|Konstanta|Hodnota|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

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

## <a name="component-selector-dialog-constants"></a>Konstanty dialogové okno Výběr součástí

|Konstanta|Hodnota|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER +. 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER +. 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER +. 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER +. 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Viz také:

- [Příkazy definované prostředím IDE pro rozšíření systémů projektů](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)