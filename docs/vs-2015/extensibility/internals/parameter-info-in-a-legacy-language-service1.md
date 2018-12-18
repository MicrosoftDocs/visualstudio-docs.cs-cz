---
title: Informace o parametrech ve starší verze jazyka1 | Dokumentace Microsoftu
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
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 462702fb73cd48f324c02344da5c5ed7c3957f23
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727942"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informace o parametrech ve službě starší verze jazyka
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Popisu tlačítka technologie IntelliSense informace o parametrech poskytuje uživatelům nápovědu, kde jsou v jazykové konstrukce.  
  
 Služby starší verze jazyka jsou implementovány jako součást sady VSPackage, ale novější způsob implementace funkce služba jazyka je pro použití rozšíření MEF. Další informace najdete v tématu [rozšíření pro Editor a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat nový editor API co nejdříve. Tím vylepšíme výkonu vaší služby jazyka a umožňují využívat nové funkce editoru.  
  
## <a name="how-parameter-info-tooltips-work"></a>Jak fungují popisky informace o parametru  
 Po zadání příkazu v editoru sady VSPackage zobrazí okno malé popisku obsahující definici příkazu uživatel píše. Například, pokud zadáte příkaz Microsoft Foundation Classes (MFC) (například `pMainFrame ->UpdateWindow`) a stisknutím klávesy otevírací závorkou zahajte seznam parametrů, návrhy metod zobrazí definici `UpdateWindow` metody.  
  
 Parametr informacích se obvykle používají ve spojení s dokončování příkazů. Jsou nejvhodnější pro jazyky, které mají parametry nebo jiné formátovaný informace po názvu metody nebo – klíčové slovo.  
  
 Informace o parametru popisky lze inicializovat pomocí služby jazyka pomocí zachycení příkazů. Aby se zachytily uživatele znaků, musí implementovat objekt služby jazyka <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a předejte mu textové zobrazení ukazatele na vaše <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementace voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metoda ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní. Příkaz filtru zachycuje příkazy, které zadáte do okna kódu. Monitorujte informace o příkazu vědět, kdy se mají zobrazit informace o parametrech pro uživatele. Stejný filtr příkaz můžete použít pro dokončování příkazů, označování chyb a tak dále.  
  
 Když zadáte – klíčové slovo, které služba jazyka může poskytnout Rady, službu jazyka vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objektu a volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metoda ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní pro oznámení rozhraní IDE zobrazíte nápovědu. Vytvořte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pomocí `VSLocalCreateInstance` a určení coclass `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` Funkce definované v souboru vsdoc.h záhlaví, která volá `QueryService` místního registru a volání `CreateInstance` na tomto objektu pro `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Poskytuje návrhy metod  
 Chcete-li poskytnout návrhy metod, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metoda v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> rozhraní, předají se jí vaši implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní.  
  
 Pokud vaše <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> třídy je vyvolána, její metody jsou volány v následujícím pořadí:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Vrátí pozice a délka související data v aktuální vyrovnávací paměti textu. Toto dá pokyn IDE není skryl tato data se okno s popisem tlačítka.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Vrátí číslo – metoda (index založený na nule), které chcete zobrazit původně. Například pokud vrátíte nula, pak první přetížená metoda se zpočátku zobrazí.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Vrátí počet přetěžované metody, které se dají použít v aktuálním kontextu. Pokud vrátí hodnotu větší než 1 pro tuto metodu, pak textové zobrazení zobrazí šipky nahoru a dolů za vás. Pokud kliknete na šipku dolů, zavolá rozhraní IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metody. Pokud kliknete na šipku nahoru, zavolá rozhraní IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Text popisu tlačítka informace o parametru je vytvořený během několik volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Vrátí počet parametrů pro zobrazení v metodě.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Pokud je metoda číslo odpovídající přetížení, které chcete zobrazit, tato metoda je volána, za nímž následuje volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informuje o službě language aktualizovat editoru, když se zobrazí návrhy metod. V <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metoda, zavolejte následující:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Přijímat volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metoda při zavření okna tip metody.

