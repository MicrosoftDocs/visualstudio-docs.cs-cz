---
title: Informace o parametrech ve službě staršího jazyka1 | Dokumenty společnosti Microsoft
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
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706791"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informace o parametrech ve službě starší verze jazyka
Popisek Informace o parametrech technologie IntelliSense poskytuje uživatelům rady o tom, kde se nacházejí v jazykové konstrukci.

 Starší jazykové služby jsou implementovány jako součást VSPackage, ale novější způsob implementace funkcí služby jazyka je použití rozšíření MEF. Další informace naleznete v [tématu Rozšíření editoru a jazykových služeb](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Doporučujeme, abyste co nejdříve začali používat nové rozhraní API editoru. Tím se zlepší výkon služby jazyka a umožní vám využít nové funkce editoru.

## <a name="how-parameter-info-tooltips-work"></a>Jak fungují popisy informací o parametrech
 Když zadáte příkaz v editoru, VSPackage zobrazí malé okno s popisem obsahující definici příkazu, který je zadáván. Pokud například zadáte příkaz Třídy microsoft foundation (MFC) (například) `pMainFrame ->UpdateWindow`a stisknutím úvodní klávesy závorky zahájíte výpis `UpdateWindow` parametrů, zobrazí se tip metody zobrazující definici metody.

 Popisky Informace o parametrech se obvykle používají ve spojení s dokončením příkazu. Jsou nejužitečnější pro jazyky, které mají parametry nebo jiné formátované informace za názvem metody nebo klíčovéslovo.

 Popisky Informace o parametrech jsou iniciovány jazykovou službou prostřednictvím zachycení příkazů. Chcete-li zachytit uživatelské znaky, objekt <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> služby jazyka musí implementovat <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> rozhraní a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> předat zobrazení <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> textu ukazatel na implementaci voláním metody v rozhraní. Filtr příkazů zachycuje příkazy, které zadáte do okna kódu. Sledujte informace o příkazech, abyste věděli, kdy se mají uživateli zobrazit informace o parametrech. Můžete použít stejný filtr příkazů pro dokončení příkazu, značky chyb a tak dále.

 Když zadáte klíčové slovo, pro které může jazyková služba poskytnout <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> rady, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> služba jazyka <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> vytvoří objekt a zavolá metodu v rozhraní, která upozorní rozhraní IDE na zobrazení nápovědy. Vytvořte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> objekt `VSLocalCreateInstance` pomocí a určení `CLSID_VsMethodTipWindow`mandatáře . `VsLocalCreateInstance`je funkce definovaná v souboru záhlaví vsdoc.h, která volá `QueryService` místní registr a volá `CreateInstance` tento objekt pro `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>Poskytnutí tipu metody
 Chcete-li poskytnout tip <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> metody, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> volání metody v rozhraní, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> předání mne implementace rozhraní.

 Když <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> je vaše třída vyvolána, její metody jsou volány v následujícím pořadí:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Vrátí pozici a délku příslušných dat v aktuální textové vyrovnávací paměti. To instruuje ide není obsemita data s panelem nástrojů.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Vrátí číslo metody (index založený na nule), který chcete zobrazit zpočátku. Například pokud vrátíte nulu, pak první přetížené metoda je zpočátku prezentovány.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Vrátí počet přetížených metod, které jsou použitelné v aktuálním kontextu. Pokud pro tuto metodu vrátíte hodnotu větší než 1, zobrazí se pro vás zobrazení textu šipky nahoru a dolů. Pokud kliknete na šipku dolů, ide volá metodu. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> Pokud kliknete na šipku nahoru, ide volá metodu. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A>

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Text popisku Informace o parametrech je vytvořen <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> během <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> několika volání metod a.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Vrátí počet parametrů, které se mají zobrazit v metodě.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Pokud vrátíte číslo metody odpovídající přetížení, které chcete zobrazit, tato metoda je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> volána, následuje volání metody.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Informuje vaši jazykovou službu aktualizovat editor při zobrazení tip metody. V <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> metodě volejte následující:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Obdržíte volání metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> při zavření okna tip metody.
