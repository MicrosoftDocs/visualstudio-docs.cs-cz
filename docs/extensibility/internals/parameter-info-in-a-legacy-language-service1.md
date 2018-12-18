---
title: Informace o parametrech v Service1 jazyk starší verze | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50450d1968c626e0a5b32dee4c6f03d005d6ede9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132760"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informace o parametrech ve službě jazyk starší verze
Informace o parametrech IntelliSense popisek poskytuje uživatelům nápovědu, jak tam, kde jsou v konstrukce jazyka.  
  
 Starší verze jazyka služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkce služby jazyk je použití MEF rozšíření. Další informace naleznete v tématu [rozšíření pro Editor a služby, jazyk](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Doporučujeme vám, že začnete používat co nejdříve editoru nové rozhraní API. Tím zvýšit výkon služby jazyk a umožňují využívat výhod nových funkcí editoru.  
  
## <a name="how-parameter-info-tooltips-work"></a>Jak fungují informace o parametru popisy tlačítek  
 Když zadáte příkaz v editoru, VSPackage zobrazí okno malé popisu obsahující definice příkaz při zadávání. Například, pokud zadáte příkaz Microsoft Foundation třídy (MFC) (například `pMainFrame ->UpdateWindow`) a stiskněte klávesu levé závorky klíče zahájíte seznam parametrů, metoda tip se zobrazí zobrazení definice `UpdateWindow` metoda.  
  
 Popisy tlačítek informace o parametru se obvykle používá ve spojení s dokončením příkazu. Jsou velmi užitečné pro jazyky, které mají parametry nebo jiné formátovaný informace po název metody nebo – klíčové slovo.  
  
 Popisy tlačítek informace o parametrech zahájili služba jazyka prostřednictvím příkazu zachycení. Zachytávat uživatele znaků, musí implementovat objekt služby váš jazyk <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a předejte textového zobrazení ukazatele na vaše <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementace voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metoda v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní. Příkaz filtru zachytí příkazy, které zadáte do okna kódu. Sledování informací o příkazu vědět, kdy se mají zobrazit informace o parametrech uživateli. Stejný filtr příkaz můžete použít pro dokončování příkazů, chyba značky a tak dále.  
  
 Klíčové slovo, pro kterou služba jazyka může poskytovat, pak službu jazyka, vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objekt a volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metoda v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní oznámit IDE zobrazíte nápovědu. Vytvořte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> pomocí `VSLocalCreateInstance` a zadání coclass `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` je funkci definovanou v vsdoc.h záhlaví souboru, který volá `QueryService` místním registru a volání `CreateInstance` na tomto objektu pro `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Poskytnutí Tip – metoda  
 Zajistit tip metoda volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metoda v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> rozhraní, předání vaši implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní.  
  
 Pokud vaše <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> třída je volána, její metody jsou označovány jako v následujícím pořadí:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Vrátí pozice a délka příslušných dat v aktuální textové vyrovnávací paměti. Tím se nastaví IDE není nesrozumitelné dat s okno popisu.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Vrátí číslo – metoda (index počítaný od nuly), které mají být zobrazeny původně. Například pokud vrátíte nula, pak první přetížené metody se nejprve zobrazí.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Vrátí počet přetížené metody, které se dají použít v aktuálním kontextu. Pokud vrátí hodnotu větší než 1. pro tuto metodu, pak textového zobrazení zobrazí nahoru a dolů dvojice šipek, které pro vás. Pokud kliknete na šipku dolů, zavolá rozhraní IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metoda. Pokud kliknete na šipku nahoru, zavolá rozhraní IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metoda.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Text popisu tlačítka informace o parametrech je vytvořený během několik volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metody.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Vrátí počet parametrů pro zobrazení v metodě.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Pokud vrátíte číslo metoda odpovídající pomocí přetížení, které chcete zobrazit, tato metoda je volána, za nímž následuje volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metoda.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Informuje o službě jazyka aktualizace editoru, když se zobrazí tip metoda. V <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody volání následující:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Přijímat volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> metoda při zavření okna tip metoda.