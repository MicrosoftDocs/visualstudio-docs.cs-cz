---
title: 'Postupy: hostování editoru v jiném editoru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204166"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Postupy: Hostování editoru v jiném editoru
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V aplikaci Visual Studio můžete hostovat jeden editor uvnitř jiného zadáním hostitelského okna jako nadřazeného okna. Chcete-li to provést, nastavte parametry <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> v podřízeném rámečku okna.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Nastavení rámce okna pro hostování editoru  
  
1. Určete editor jako hostovaný Editor vytvořením podřízeného podokna okna.  
  
     V tomto podokně se nachází text editoru.  
  
2. Vytvořte Editor hostování pomocí <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> metody nebo.  
  
3. Nastavte <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> vlastnosti a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> v rámci implementace rámce okna hostovaného editoru předáním těchto vlastností jako parametrů <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> metody v uvedeném pořadí.  
  
     Pokud potřebujete tyto parametry načíst, předejte tyto vlastnosti <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodě.  
  
4. Zavolejte <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodu pro obsažený Editor.  
  
     Editor se zobrazí v hostovaném podokně obsahujícího Editor.  
  
## <a name="robust-programming"></a>Robustní programování  
 **Návrhář aplikací** v rámci Visual Studio Team Edition pro architekty je příkladem rámce okna editoru hostujícího jiný Editor. **Návrhář aplikací** hostuje jiné návrháře v pravém podokně. Panel návrháře (nebo stránka **vlastností** ) pro každý z obsažených návrhářů je přidán do obsahujícího rámce okna.
