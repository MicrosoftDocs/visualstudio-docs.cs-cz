---
title: 'Postupy: Přidání standardní Text značky | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dd34b14b89c78d01f1d4acab57f33014860d7ba
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39638817"
---
# <a name="how-to-add-standard-text-markers"></a>Postupy: Přidání standardní text značky
Pomocí následujícího postupu vytvořte jeden výchozí typ značky text, opatřeného [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] základní editor.  
  
## <a name="to-create-a-text-marker"></a>Chcete-li vytvořit text značky  
  
1.  V závislosti na tom, zda používáte jeden nebo two trojrozměrným systém souřadnic, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metoda nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodu pro vytvoření nové značky text.  
  
     Při volání této metody určete typ značky, rozsah textu pro vytvoření značky nad a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní. Tato metoda pak vrací ukazatel na nově vytvořený text značky. Typy značek pocházejí ze <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> výčtu. Zadejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, pokud chcete být informováni o událostech.  
  
    > [!NOTE]
    >  Vytvoření textu značky na pouze hlavní vlákno uživatelského rozhraní. Základní editor spoléhá na obsah vyrovnávací paměť textu pro vytvoření textu značek a textovou vyrovnávací paměť není bezpečné pro vlákna.  
  
## <a name="add-a-custom-command"></a>Přidat vlastní příkaz.  
 Implementace `IVsTextMarkerClient` rozhraní a poskytuje ukazatel na ni z značku zlepšuje chování značky několika způsoby. Nejprve díky tomu můžete zajistit tipy pro vaši značku a příkazy. To vám také umožní příjem oznámení o události pro jednotlivé značky a vytvářet vlastní místní nabídky přes značky. Pomocí následujícího postupu přidejte vlastní příkaz na místní nabídku značky.  
  
### <a name="to-add-a-custom-command-to-the-context-menu"></a>Chcete-li přidat vlastní příkaz do kontextové nabídky  
  
1.  Před zobrazením v místní nabídce prostředí volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> – metoda a předá je ukazatel na text značky vliv a počet položky příkazu v místní nabídce.  
  
     Například obsahovat příkazů specifických pro zarážku v místní nabídce **odebrat zarážku** prostřednictvím **Nová zarážka**, jako je zobrazena na následujícím snímku obrazovky.  
  
     ![Místní nabídka značky](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2.  Předávání zpátky nějaký text rozlišujícího názvu vlastní příkaz. Například **odebrat zarážku** může být vlastní příkaz, pokud prostředí už neposkytl ho. Můžete také předat zpět Určuje, zda je příkazu podporované, zpřístupnění a povolení a přepínání zapnutí nebo vypnutí. Prostředí používá tyto informace k zobrazení vlastního příkazu v místní nabídce správným způsobem.  
  
3.  Ke spuštění příkazu prostředí volání <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metoda předání ukazatele text značky a počet vybraný v místní nabídce příkaz.  
  
     Tyto informace z tohoto volání použijte k provedení libovolné akce text značky určuje vlastní příkaz.  
  
## <a name="see-also"></a>Viz také:  
 [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: implementace označování chyb](../extensibility/how-to-implement-error-markers.md)   
 [Postupy: vytvoření vlastního textu značky](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: použití značek text](../extensibility/how-to-use-text-markers.md)