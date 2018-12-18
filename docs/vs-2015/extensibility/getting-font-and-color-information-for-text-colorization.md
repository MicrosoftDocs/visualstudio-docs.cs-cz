---
title: Písma a barvy informace pro barevné zvýraznění textu | Dokumentace Microsoftu
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
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 41fc6ac7ba20bc552ebdfde2cab69dd28867ee7f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741305"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Písma a barvy informace pro barevné zvýraznění textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces, který vykreslí nebo barevně zvýrazněné text se zobrazí prvky uživatelského rozhraní (UI) závisí na typu projektu, technologie a developer předvolby. **Písma a barvy** stránku vlastností ukládá nastavení.  
  
 Většina implementací, které se zobrazí text barevně zvýrazněné potřebují `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` a přidružené rozhraní pro nastavení zobrazení prezentace, načítání a ukládání textu.  
  
> [!NOTE]
>  Při přizpůsobování základní editor (která podporuje **Text EditorCategory**), důrazně doporučujeme používat technologii barevné zvýraznění ve službě jazyka. Další informace najdete v tématu [písma a barvy přehled](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Získání výchozí písmo a barvy informace  
 Všechny **písma a barvy** nastavení jakékoli okno zobrazení textu musí být zadán v **zobrazit položky** jednoho **kategorie**. Další informace najdete v tématu [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Barevně zvýrazňovat, musíte získat VSPackage aktuální **písma a barvy** nastavení. VSPackage můžete to udělat následujícími způsoby v závislosti na svých potřeb:  
  
- Pomocí mechanismu trvalosti písma a barvy uložené nebo aktuální stav. Další informace najdete v tématu [přístup k uložené písmo a barvy nastavení](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Použití <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní službu poskytující data písma a barvy, abyste získali instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>, nejsou-li sady VSPackage také poskytovatele písmo a barvu.  
  
- Implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> rozhraní.  
  
  Chcete-li zajistit, aby získala při dotazování na výsledky jsou aktuální, může být vhodné použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní k určení, zda aktualizace je nutné před voláním metody načítání <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.  
  
  Poté co získané informace písma a barvy, analyzovat text, který má být zobrazen za účelem identifikování prvky vyžaduje zabarvování a text pak můžete zobrazit v okně pomocí odpovídající písma a barvy.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Použití písem a textu](http://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Práce s barvou](http://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [Rozhraní GDI (graphics zařízení rozhraní)](http://msdn.microsoft.com/en-us/7e1d4540-bb2e-4257-8eee-eee376acba83)

