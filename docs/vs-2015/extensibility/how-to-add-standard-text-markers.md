---
title: 'Postupy: Přidání standardních značek textu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - standard text markers
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 912d5d7a225520fc825d832bf73f5cfc733a9486
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64780698"
---
# <a name="how-to-add-standard-text-markers"></a>Postupy: Přidání standardních textových značek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí následujícího postupu můžete vytvořit jeden z výchozích typů textových značek, který je součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] základního editoru.  
  
### <a name="to-create-a-text-marker"></a>Vytvoření značky textu  
  
1. V závislosti na tom, zda používáte jeden nebo dvojrozměrné systém souřadnic, zavolejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> metodu nebo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A> metodu pro vytvoření nové značky textu.  
  
     V tomto volání metody zadejte typ značky, rozsah textu, který má být vytvořen a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní. Tato metoda potom vrátí ukazatel na nově vytvořenou značku textu. Typy značek jsou odebírány z <xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE> výčtu. Určete <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> rozhraní, pokud chcete být informováni o událostech značek.  
  
    > [!NOTE]
    > Vytváření textových značek pouze v hlavním vlákně uživatelského rozhraní. Základní editor spoléhá na obsah vyrovnávací paměti textu pro vytváření textových značek a textová vyrovnávací paměť není bezpečná pro přístup z více vláken.  
  
## <a name="adding-a-custom-command"></a>Přidání vlastního příkazu  
 Implementace `IVsTextMarkerClient` rozhraní a poskytnutí ukazatele na něj z značky vylepšuje chování značky několika způsoby. Nejprve vám umožní zadat tipy pro vaši značku a spustit příkazy. To vám také umožní přijímat oznámení o událostech pro jednotlivé značky a vytvořit vlastní kontextovou nabídku nad značkou. Pomocí následujícího postupu můžete přidat vlastní příkaz do místní nabídky značek.  
  
#### <a name="to-add-a-custom-command-to-the-context-menu"></a>Přidání vlastního příkazu do místní nabídky  
  
1. Před zobrazením kontextové nabídky prostředí zavolá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A> metodu a předá ukazatel na ovlivněnou textovou značku a číslo položky příkazu v místní nabídce.  
  
     Například příkazy specifické pro zarážku v kontextové nabídce zahrnují **odebrat zarážku** prostřednictvím **nové zarážky**, jak je znázorněno na následujícím snímku obrazovky.  
  
     ![Kontextová nabídka značky](../extensibility/media/vsmarkercontextmenu.gif "vsMarkercontextmenu")  
  
2. Předejte nějaký text, který identifikuje název vlastního příkazu. Například **odebrat zarážku** může být vlastní příkaz, pokud ho prostředí ještě neposkytlo. Předáte také, jestli je příkaz podporovaný, dostupný a povolený, nebo přepínač zapnutý. Prostředí používá tyto informace k tomu, aby zobrazoval vlastní příkaz v místní nabídce správným způsobem.  
  
3. Chcete-li spustit příkaz, prostředí volá <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A> metodu, předá ukazatel na značku textu a číslo příkazu vybraného z kontextové nabídky.  
  
     Tyto informace z tohoto volání slouží k provedení jakékoli akce značky textu, kterou vlastní příkaz nadiktuje.  
  
## <a name="see-also"></a>Viz také  
 [Používání textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: implementace značek chyb](../extensibility/how-to-implement-error-markers.md)   
 [Postupy: vytváření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: Použití textových značek](../extensibility/how-to-use-text-markers.md)
