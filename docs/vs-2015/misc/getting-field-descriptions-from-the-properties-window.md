---
title: Získání popisů polí z okna vlastností | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703972"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Získání popisů polí z okna vlastností
V dolní části okna **vlastnosti** se v oblasti popis zobrazí informace související s vybraným polem vlastností. Tato funkce je ve výchozím nastavení zapnutá. Chcete-li skrýt pole Popis, klikněte pravým tlačítkem myši na okno **vlastnosti** a klikněte na položku **Popis**. Tím se také zruší zaškrtnutí vedle nadpisu **Popis** v okně nabídky. Toto pole můžete znovu zobrazit podle stejného postupu, abyste mohli **Popis** znovu zapnout.  
  
 Informace v poli Popis pocházejí z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Každá metoda, rozhraní, třída typu coclass a podobně může mít nemístní `helpstring` atribut v knihovně typů. Okno **vlastnosti** načte řetězec z <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .  
  
### <a name="to-specify-localized-help-strings"></a>Určení lokalizovaných řetězců v nápovědě  
  
1. Přidejte `helpstringdll` atribut do příkazu Library v knihovně typů ( `typelib` ).  
  
   > [!NOTE]
   > Tento krok je nepovinný, pokud se knihovna typů nachází v souboru knihovny objektů (. olb).  
  
2. Zadejte `helpstringcontext` atributy pro řetězce. Můžete také zadat `helpstring` atributy.  
  
    Tyto atributy jsou odlišné od `helpfile` atributů a `helpcontext` , které jsou obsaženy v tématech nápovědy k souboru skutečných souborů. chm.  
  
   Chcete-li načíst informace o popisu, který má být zobrazen pro zvýrazněný název vlastnosti, okno **vlastností** vyvolá <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> vlastnost, která je vybrána, a určí požadovaný `lcid` atribut pro výstupní řetězec. Interně <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> nalezne soubor. dll zadaný v `helpstringdll` atributu a volání `DLLGetDocumentation` daného souboru. dll se zadaným kontextem a `lcid` atributem.  
  
   Signatura a implementace nástroje `DLLGetDocumentation` jsou:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation`Funkce musí být export definovaný v souboru. def pro knihovnu DLL.  
  
 Interně se vytvoří soubor. olb, který je ve skutečnosti knihovnou DLL. Tato knihovna DLL obsahuje jeden prostředek, soubor knihovny typů (. tlb) a jednu exportovanou funkci `DLLGetDocumentation` .  
  
 V případě souborů. olb `helpstringdll` je atribut volitelný, protože se jedná o stejný soubor, který obsahuje samotný soubor. tlb.  
  
 Chcete-li získat řetězce, které se mají zobrazit v podokně **popisy** , tak minimum, které musíte udělat, je určit `helpstring` atribut v knihovně typů. Pokud chcete, aby byly tyto řetězce lokalizovány, je nutné zadat `helpstringdll` atribut (volitelné) a `helpstringcontext` atribut (Required) a implementovat `DLLGetDocumentation` .  
  
 Neexistují žádná další rozhraní, která je nutné implementovat při získávání lokalizovaných informací prostřednictvím `helpstringcontext` atributu IDL a `DLLGetDocumentation` .  
  
 Dalším způsobem získání lokalizovaného názvu a popisu vlastnosti je implementace <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Další informace o implementaci této metody naleznete v části [pole a rozhraní okna vlastnosti](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Pole a rozhraní okna vlastností](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Rozšíření vlastností](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [atribut HelpContext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [soubor](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)