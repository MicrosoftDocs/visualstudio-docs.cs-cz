---
title: Přístup k vyrovnávací paměti textu s použitím rozhraní API pro starší verze | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3347fc2fd03a2eb6b466145672d3aebb77ad71a6
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2018
ms.locfileid: "39078011"
---
# <a name="access-the-text-buffer-by-using-the-legacy-api"></a>Přístup k vyrovnávací paměti textu pomocí starší verze rozhraní API
Text zodpovídá za správu textových datových proudů a trvalost souborů. I když vyrovnávací paměti může číst nebo zapisovat dalších formátů, všechny běžné komunikaci s vyrovnávací paměť je prováděno pomocí kódování Unicode. Ve starší verzi rozhraní API můžete textovou vyrovnávací paměť použít buď jeden – nebo dvojrozměrné souřadnicový systém k identifikaci umístění znaku ve vyrovnávací paměti.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Jeden a dvě dimenze koordinovat systémy  
 Jednorozměrný souřadnice polohy je založená na pozici znaku od prvního znaku ve vyrovnávací paměti, jako je například 147. Můžete použít <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> rozhraní pro přístup k jednorozměrné umístění ve vyrovnávací paměti. Dvojrozměrné souřadnice systém je založen na dvojice řádku a indexu. Například znak ve vyrovnávací paměti na 43 by být 5 na řádku 43 pět znaků napravo od prvního znaku v daném řádku. Přístup k dvojrozměrné umístění ve vyrovnávací paměti pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní. Jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> rozhraní implementují objekt vyrovnávací paměti textu (<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>) a je přístupný od sebe navzájem pomocí `QueryInterface`. Následující diagram znázorňuje tyto a další klíče rozhraní na <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>.  
  
 ![Objekt vyrovnávací paměti textu](../extensibility/media/vstextbuffer.gif "vstextbuffer –")  
Objekt vyrovnávací paměť textu  
  
 Přestože buď souřadnicový systém funguje ve vyrovnávací paměti textu, je optimalizován pro použití dvojrozměrné souřadnice. Jednorozměrný souřadnicový systém můžete vytvořit nároky na výkon. Proto systém dvojrozměrné souřadnice kdykoli je to možné.  
  
 Trvalost souborů je text druhého odpovědnost přípravné vyrovnávací paměti. K tomuto účelu implementuje objekt vyrovnávací paměti textu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> a funguje jako součást objektu data dokumentů pro položky projektu a další prostředí součásti účastnící se trvalosti. Další informace najdete v tématu [otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Změna nastavení zobrazení pomocí starší verze rozhraní API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Vysvětluje, jak změnit nastavení zobrazení pomocí starší verze rozhraní API.  
  
 [Pomocí Správce text můžete sledovat globální nastavení](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Vysvětluje, jak použít textový správce k monitorování globální nastavení.  
  
## <a name="see-also"></a>Viz také:  
 [V editoru core](../extensibility/inside-the-core-editor.md)