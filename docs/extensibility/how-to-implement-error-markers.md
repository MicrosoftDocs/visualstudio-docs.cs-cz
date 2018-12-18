---
title: 'Postupy: implementace označování chyb | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: eb6e511fa899680338831f3bc8e2a411f2126006
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861160"
---
# <a name="how-to-implement-error-markers"></a>Postupy: implementace označování chyb
Označování chyb (nebo červené podtržení vlnovkou) jsou nejobtížnější přizpůsobení editoru textu k implementaci. Však výhody, které nabízejí uživatelům vaší VSPackage můžete mnohem převažují nad náklady a umožnit jim. Označování chyb myš označit text, který předpokládá, že nesprávné s podtržení nebo podtrženo červenou čáru vaše analyzátoru jazyka. Tento ukazatel pomáhá programátoři vizuálně zobrazením nesprávný kód.  
  
 Použití značek text k implementaci červené podtržení vlnovkou. Zpravidla jazykové služby přidat červené podtržení vlnovkou do vyrovnávací paměti textu jako pozadí pass, v době nečinnosti nebo ve vlákně na pozadí.  
  
## <a name="to-implement-the-red-wavy-underline-feature"></a>Chcete-li implementovat funkci červenou vlnovkou  
  
1. Vyberte text, u které chcete umístit červenou vlnovkou.  
  
2. Vytvořit značku typu `MARKER_CODESENSE_ERROR`. Další informace najdete v tématu [postupy: Přidání standardní text značky](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Potom předejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ukazatel rozhraní.  
  
   Tento proces také umožňuje vytvořit text tipu nebo speciální kontextové nabídky přes danou značku. Další informace najdete v tématu [postupy: Přidání standardní text značky](../extensibility/how-to-add-standard-text-markers.md).  
  
   Následující objekty jsou požadovány, než lze zobrazit označování chyb.  
  
- Analyzátor.  
  
- Zprostředkovatel úkolu (to znamená, že implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>), který udržuje záznam změn v řádku informace za účelem zjištění znovu analyzovaný řádky.  
  
- Filtr zobrazení textu, který zachycuje blikající kurzor o události změn pomocí zobrazení <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A>) metody.  
  
  Analyzátor, zprostředkovatel úkolu a filtr poskytují infrastrukturu nutnou k umožnění označování chyb. Následující kroky obsahují procesu pro zobrazení označování chyb.  
  
1.  V zobrazení se filtruje je filtr získá ukazatel na úkol zprostředkovatele spojeného s data tohoto zobrazení.  
  
    > [!NOTE]
    >  Stejný filtr příkaz můžete použít pro metodu tipy, dokončování příkazů, označování chyb a tak dále.  
  
2.  Když filtr dostane událost označující, že přesunete na jiný řádek, vytvoří se úkol ke kontrole chyb.  
  
3.  Obslužná rutina úkol zkontroluje, jestli řádku změny. Pokud ano, analyzuje řádku chyby.  
  
4.  Pokud byly zjištěny chyby, zprostředkovatel úkolu vytvoří instanci položky úkolu. Tato instance vytvoří značku text, který používá prostředí jako značka chyby v zobrazení textu.  
  
## <a name="see-also"></a>Viz také:  
 [Text značky pomocí starší verze rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardní text značky](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: vytvoření vlastního textu značky](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: použití značek text](../extensibility/how-to-use-text-markers.md)
