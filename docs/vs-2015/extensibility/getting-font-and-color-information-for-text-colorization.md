---
title: Získávání informací o písmech a barvách pro barevné nabarvení textu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- text, coloring
- font and color control [Visual Studio SDK], coloring
ms.assetid: d1f985bd-743e-40b7-9458-d9af53647c91
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8724c31accb26e478c2726dfe791256994fc95ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696859"
---
# <a name="getting-font-and-color-information-for-text-colorization"></a>Získání informací o písmu a barvě pro obarvení textu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Proces, který vykresluje nebo zobrazuje barevný text v prvcích uživatelského rozhraní (UI), závisí na typu projektu, jeho technologie a vývojářích pro vývojáře. Nastavení se uloží na stránce vlastností **písma a barvy** .  
  
 Většina implementací, které zobrazují barevný text, potřebují `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` a přidružená rozhraní pro prezentace, načítání a ukládání nastavení zobrazení textu.  
  
> [!NOTE]
> Při přizpůsobování základního editoru (který podporuje **text EditorCategory**) se důrazně doporučuje používat technologii vybarvení ve službě jazyka. Další informace najdete v tématu [Přehled písma a barev](../extensibility/font-and-color-overview.md).  
  
## <a name="getting-default-font-and-color-information"></a>Získávání výchozích informací o písmech a barvách  
 Všechna nastavení **písem a barev** libovolného okna zobrazující text by se měla zadat v **položkách zobrazení** jedné **kategorie**. Další informace najdete v tématu [písma a barvy, prostředí, dialogové okno Možnosti](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
 Pro zabarvovat musí VSPackage získat aktuální nastavení **písem a barev** . VSPackage může dosáhnout následujícími způsoby v závislosti na svých potřebách:  
  
- Použijte mechanismus písma a trvalosti barev k načtení uloženého nebo aktuálního stavu. Další informace najdete v tématu [přístup k uloženým písmům a nastavením barev](../extensibility/accessing-stored-font-and-color-settings.md).  
  
- Použijte <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> rozhraní služby poskytující data písma a barev k získání instance <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> , pokud VSPackage není zároveň poskytovatelem písma a barvy.  
  
- Implementujte rozhraní <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>.  
  
  Aby bylo zajištěno, že výsledky získané cykly jsou aktuální, může být užitečné použít <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> rozhraní k určení, zda je aktualizace požadována před voláním metod načtení <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> rozhraní.  
  
  Po získání informací o písmech a barvách Analyzujte text, který se má zobrazit, abyste identifikovali prvky vyžadující zabarvení a pak text v okně zobrazili pomocí příslušných písem a barev.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 [Používání písma a textu](https://msdn.microsoft.com/library/d43640f3-da94-4df2-a29d-a9d021a1c069)   
 [Práce s barvou](https://msdn.microsoft.com/library/d34ff96f-241d-494f-abdd-13811ada8cd3)   
 [GDI (grafické rozhraní zařízení)](https://msdn.microsoft.com/7e1d4540-bb2e-4257-8eee-eee376acba83)
