---
title: Informace o parametrech ve starším jazyce Service1 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f8e5664634d189e8463376761d8fb59543740df
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2020
ms.locfileid: "88238072"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Informace o parametrech ve službě starší verze jazyka 1
Popis parametrů technologie IntelliSense poskytuje uživatelům odkazy na to, kde jsou v jazykové konstrukci.

 Starší jazykové služby jsou implementovány jako součást sady VSPackage, ale novější způsob, jak implementovat funkce jazykové služby, je použít rozšíření MEF. Další informace najdete v tématu [rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme začít používat nové rozhraní API editoru co nejrychleji. Tím se vylepšit výkon vaší jazykové služby a umožní vám využít nové funkce editoru.

## <a name="how-parameter-info-tooltips-work"></a>Jak fungují popisky informací o parametrech
 Při psaní příkazu v editoru, VSPackage zobrazí malé okno s popisem obsahující definici příkazu, který se má napsat. Například pokud zadáte příkaz Microsoft Foundation Classes (MFC) (například `pMainFrame ->UpdateWindow` ) a stisknete klávesu otevírací závorky k zahájení výpisu parametrů, zobrazí se popis metody se zobrazením definice `UpdateWindow` metody.

 Popisky informací o parametrech se obvykle používají ve spojení s dokončováním příkazů. Jsou nejužitečnější pro jazyky, které mají parametry nebo jiné formátované informace za názvem metody nebo klíčovým slovem.

 Popisy parametrů jsou iniciovány pomocí služby jazyka prostřednictvím zachycení příkazu. Pro zachycení uživatelských znaků objekt služby jazyka musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a předat textové zobrazení ukazatele na vaši <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> implementaci voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní. Filtr příkazu zachycuje příkazy, které zadáte do okna Code (kód). Sledujte informace o příkazu a zjistěte, kdy zobrazit informace o parametrech pro uživatele. Můžete použít stejný filtr příkazů pro dokončování příkazů, značky chyb a tak dále.

 Po zadání klíčového slova, pro které může služba jazyka poskytnout nápovědu, pak služba jazyka vytvoří <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objekt a zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> metodu v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> rozhraní, aby zobrazila NÁPOVĚDU pro rozhraní IDE. Vytvořte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objekt pomocí `VSLocalCreateInstance` a zadáním coclass `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance` je funkce definovaná v hlavičkovém souboru vsdoc. h, který volá `QueryService` místní registr a volá `CreateInstance` Tento objekt pro `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Poskytnutí popisu metody
 Chcete-li zadat Tip metody, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metodu v <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> rozhraní a předejte jí implementaci <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> rozhraní.

 Když <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> je třída vyvolána, jejich metody jsou volány v následujícím pořadí:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Vrátí pozici a délku relevantních dat v aktuální vyrovnávací paměti textu. Rozhraní IDE tak vydá pokyn, aby tato data neskryla pomocí okna s popisem tlačítka.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Vrátí číslo metody (index založený na nule), který chcete zobrazit zpočátku. Například pokud vrátíte hodnotu nula, první přetížená metoda se zpočátku prezentuje.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Vrátí počet přetížených metod, které jsou použity v aktuálním kontextu. Pokud pro tuto metodu vrátíte hodnotu větší než 1, zobrazí se v zobrazení text šipky nahoru a dolů. Pokud kliknete na šipku dolů, rozhraní IDE volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> metodu. Pokud kliknete na šipku nahoru, rozhraní IDE volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> metodu.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Text popisu parametru je vytvořen během několika volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> metod a.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Vrátí počet parametrů, které se mají zobrazit v metodě.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Pokud vrátíte číslo metody odpovídající přetížení, které chcete zobrazit, je volána Tato metoda následovaná voláním <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metody.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informuje vaši jazykovou službu, aby aktualizovala Editor při zobrazení tipu metody. V <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodě zavolejte následující:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>Po zavření okna s popisem metody obdržíte volání metody.
