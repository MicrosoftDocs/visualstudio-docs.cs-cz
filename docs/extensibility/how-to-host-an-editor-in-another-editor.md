---
title: 'Postupy: hostování editoru jiného editoru | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53b4f02135b18c4641d4e802df3d1124a5d06b47
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37058383"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Postupy: hostování editoru jiného editoru

V sadě Visual Studio můžete hostovat jeden editor uvnitř jiné zadáním okno hostování jako nadřazeného okna. Chcete-li tak učinit, nastavit parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> na rámec okna podřízené.

## <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Nastavit rámce okna pro hostování editoru

1.  Určete editoru jako hostované editor vytvořením podokna a podřízené.

     Toto podokno je, kde bude přejděte text editoru.

2.  Vytvoření hostujícím editorem pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> nebo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metoda.

3.  Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentHwnd> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2.VSFPROPID_ParentFrame> vlastnosti implementace rámce okna editoru hostované předáním tyto vlastnosti jako parametry, které chcete <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metoda, v uvedeném pořadí.

     Pokud potřebujete k načtení těchto parametrů, předejte tyto vlastnosti, které chcete <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metoda.

4.  Volání <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metoda pro obsažené editor.

     Editor se zobrazí v podokně hostované obsahující editoru.

## <a name="robust-programming"></a>Robustní programování

**Application Designer** ve Visual Studio Team Edition architekty je příkladem rámce okna editoru hostování jiný editor. **Application Designer** hostitelem jiných Designer v jeho pravém podokně. Návrhář panel (nebo **vlastnosti** stránky) pro každý obsažený Designer se přidá do obsahující rámec okna.