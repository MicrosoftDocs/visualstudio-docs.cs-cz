---
title: Přístup k textové vyrovnávací paměti pomocí starší verze rozhraní API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185003"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Přístup k vyrovnávací paměti textu pomocí zastaralého rozhraní API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Text zodpovídá za správu datových proudů a trvalosti souborů. I když vyrovnávací paměť může číst nebo zapisovat jiné formáty, veškerá běžná komunikace s vyrovnávací pamětí se provádí pomocí kódování Unicode. Ve starších rozhraních API může textová vyrovnávací paměť použít jeden nebo dvojrozměrné systém souřadnic k identifikaci umístění znaků ve vyrovnávací paměti.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Systémy souřadnic jednoho a dvou dimenzí  
 Jednorozměrné umístění souřadnic je založeno na pozici znaku od prvního znaku ve vyrovnávací paměti, například 147. Použijete <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> rozhraní pro přístup k jednorozměrnému umístění ve vyrovnávací paměti. Dvourozměrný systém souřadnic je založen na dvojicích řádků a indexů. Například znak v bufferu na 43, 5 znaků na řádku 43, pět znaků napravo od prvního znaku na řádku. Přistupujete k dvojrozměrnému umístění ve vyrovnávací paměti pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> rozhraní. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> Rozhraní i rozhraní jsou implementovány objektem vyrovnávací paměti textu ( <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ) a lze k nim přistupovat pomocí `QueryInterface` . Následující diagram znázorňuje tato a další klíčová rozhraní v <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Objekt textové vyrovnávací paměti](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Objekt textové vyrovnávací paměti  
  
 I když buď souřadnicový systém funguje ve vyrovnávací paměti textu, je optimalizován pro použití dvourozměrných souřadnic. Jednorozměrný systém souřadnic může vytvářet režijní náklady na výkon. Proto použijte dvojrozměrné systém souřadnic, kdykoli je to možné.  
  
 Druhá odpovědnost pro vyrovnávací paměť textu je trvalá File. K tomu objekt vyrovnávací paměti textu implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> a funguje jako komponenta datového objektu dokumentu pro položky projektu a další komponenty prostředí zapojené do trvalého uložení. Další informace naleznete v tématu [otevření a uložení položek projektu](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Změna nastavení zobrazení pomocí zastaralého rozhraní API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Vysvětluje, jak změnit nastavení zobrazení pomocí starší verze rozhraní API.  
  
 [Použití textového správce k monitorování globálního nastavení](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Vysvětluje, jak používat Správce textu k monitorování globálních nastavení..  
  
## <a name="see-also"></a>Viz také  
 [Práce v základní editoru](../extensibility/inside-the-core-editor.md)
