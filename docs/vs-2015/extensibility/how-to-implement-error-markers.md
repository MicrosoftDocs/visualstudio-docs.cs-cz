---
title: 'Postupy: implementace značek chyb | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803609"
---
# <a name="how-to-implement-error-markers"></a>Postupy: Implementace chybových značek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chybové značky (nebo červené podtržení vlnovkou) jsou nejobtížnější pro implementaci přizpůsobení textového editoru. Výhody, které poskytují uživatelům sady VSPackage, však mohou mnohem převážit náklady, aby je poskytovaly. Chybové značky označují text s dvojitou značkou, který analyzátor jazyka považuje za nesprávný, pomocí vlnovky nebo červené čáry. Tento indikátor pomáhá programátorům vizuálně zobrazovat nesprávný kód.  
  
 Použijte textové značky k implementaci červených podtržení vlnovkou. V rámci pravidla jazykové služby přidávají červeně podtržení vlnovkou do vyrovnávací paměti textu jako Pass na pozadí, a to buď v době nečinnosti, nebo ve vlákně na pozadí.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Implementace červené funkce podtržení vlnovkou  
  
1. Vyberte text, pod kterým chcete umístit červené podtržení.  
  
2. Vytvořte značku typu `MARKER_CODESENSE_ERROR` . Další informace najdete v tématu [Postup: Přidání standardních značek textu](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Potom předejte <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ukazatel rozhraní.  
  
   Tento proces také umožňuje vytvořit text tipu nebo speciální kontextovou nabídku přes danou značku. Další informace najdete v tématu [Postup: Přidání standardních značek textu](../extensibility/how-to-add-standard-text-markers.md).  
  
   Aby bylo možné zobrazit chybové značky, jsou vyžadovány následující objekty.  
  
- Analyzátor.  
  
- Poskytovatel úloh (tj. implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> ), který uchovává záznam změn v informacích o řádku, aby bylo možné identifikovat řádky, které se mají znovu analyzovat.  
  
- Filtr zobrazení textu, který zachycuje události změny blikajícího kurzoru ze zobrazení pomocí <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> metody).  
  
  Analyzátor, poskytovatel úloh a filtr poskytují infrastrukturu potřebnou k tomu, aby bylo možné zobrazit chybové značky. Následující kroky poskytují postup pro zobrazení chybových značek.  
  
1. V zobrazení, které je filtrováno, filtr získá ukazatel na poskytovatele úlohy přidruženého k datům tohoto zobrazení.  
  
    > [!NOTE]
    > Stejný filtr příkazů můžete použít pro popisy metod, dokončování příkazů, značky chyb a tak dále.  
  
2. Když filtr přijme událost, která indikuje, že jste přešli na jiný řádek, vytvoří se úkol, který zkontroluje chyby.  
  
3. Obslužná rutina úlohy zkontroluje, zda je řádek nečistý. Pokud ano, analyzuje řádek pro chyby.  
  
4. Pokud jsou nalezeny chyby, poskytovatel úlohy vytvoří instanci položky úkolu. Tato instance vytvoří značku textu, kterou prostředí používá jako značku chyby v zobrazení text.  
  
## <a name="see-also"></a>Viz také  
 [Používání textových značek se starší verzí rozhraní API](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Postupy: Přidání standardních značek textu](../extensibility/how-to-add-standard-text-markers.md)   
 [Postupy: vytváření vlastních textových značek](../extensibility/how-to-create-custom-text-markers.md)   
 [Postupy: Použití textových značek](../extensibility/how-to-use-text-markers.md)
