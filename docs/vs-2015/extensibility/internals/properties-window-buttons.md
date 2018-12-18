---
title: Tlačítka okna Vlastnosti | Dokumentace Microsoftu
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
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb6a3802e135c02b4ccc7b27aca69b2afd2a9f70
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789847"
---
# <a name="properties-window-buttons"></a>Tlačítka okna Vlastnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

V závislosti na vývojový jazyk a typ produktu, jsou některá tlačítka zobrazí ve výchozím nastavení na panelu nástrojů **vlastnosti** okna. Ve všech případech **Categorized**, **Alphabetized**, **vlastnosti**, a **stránky vlastností** tlačítek se zobrazí. V jazyce Visual C# a Visual Basic **události** je zobrazeno tlačítko. V některých projektů Visual C++ **VC ++ zprávy** a **VC přepíše** tlačítek se zobrazí. Pro ostatní typy projektů, může se zobrazit další tlačítka. Další informace o tlačítka v **vlastnosti** okna, naleznete v tématu [okno vlastností](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Provádění tlačítka okna Vlastnosti  
 Když kliknete **Categorized** tlačítko, volání sady Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> rozhraní na objekt, který má právě fokus do jeho vlastnosti seřadit podle kategorie. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> se implementuje na `IDispatch` objekt, který se zobrazí **vlastnosti** okna.  
  
 Existují 11 předdefinovanou vlastnost kategorie, které mají záporné hodnoty. Můžete definovat vlastní kategorie, ale doporučujeme vám, že budete přiřazovat kladné hodnoty, abychom je odlišili od předdefinovaným kategoriím.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Vrátí metoda hodnotu odpovídající vlastnosti kategorie pro zadanou vlastnost. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Metoda vrátí řetězec obsahující název kategorie. Stačí poskytují podporu pro vlastní hodnoty, protože Visual Studio ví hodnoty kategorie standardních vlastností.  
  
 Když kliknete **Alphabetized** tlačítko Vlastnosti jsou zobrazeny v abecedním pořadí podle názvu. Názvy jsou načítána `IDispatch` podle algoritmu lokalizované řazení.  
  
 Při **vlastnosti** otevřeném okně **vlastnosti** se automaticky zobrazí tlačítko jako vybraný. V dalších částech tohoto prostředí se zobrazí na stejné tlačítko a kliknutím na Zobrazit **vlastnosti** okna.  
  
 **Stránky vlastností** tlačítko je k dispozici Pokud `ISpecifyPropertyPages` není implementována pro vybraný objekt. Zobrazení vlastností závislé na konfiguraci, které jsou obvykle spojené s řešeními a projekty stránky vlastností projektu, ale mohou být také být spojeny s položkami projektu (například v aplikaci Visual C++).  
  
> [!NOTE]
>  Nelze přidat tlačítka panelu nástrojů **vlastnosti** okna pomocí nespravovaného kódu. Chcete-li přidat tlačítko panelu nástrojů, musíte vytvořit spravovaný objekt, který je odvozen z <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vlastností](../../extensibility/internals/extending-properties.md)

