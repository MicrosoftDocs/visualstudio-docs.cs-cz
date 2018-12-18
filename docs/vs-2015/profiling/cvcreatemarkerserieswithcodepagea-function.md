---
title: Cvcreatemarkerserieswithcodepagea – funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c25877a3ab54f70207103a2c909163807b4c2e4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51740133"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA – funkce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vytvoří značky řady pro daného poskytovatele a zadaný znakovou stránku. Tato funkce slouží k určení znakovou stránku explicitně pro textu zapsaného funkce rozhraní API ANSI značky. Nastavení znakové stránky může být užitečné v případě trasování je zachycena a potom analyzovány na odlišných počítačích s různými národní prostředí nebo jazyky. Ve výchozím nastavení se používá znakovou stránku vrácená funkcí GetACP().  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProvider`  
 Cvinitprovider – dříve inicializován objekt zprostředkovatele. Nemůže mít hodnotu NULL.  
  
 `pSeriesName`  
 Název značky řady. Nemůže mít hodnotu NULL, ale je povolen prázdný řetězec.  
  
 `nTextCodePage`  
 Platný znakovou stránku.  
  
 `ppMarkerSeries`  
 Adresa výstupní proměnné, která bude ukládat značky řady kontextu. Nemůže mít hodnotu NULL.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK při úspěšném vytvoření značky řady nebo kód chyby v případě, že existuje byly všechny chyby. Použití makra SUCCEEDED nebo FAILED zkontrolujte chybovou podmínku.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** cvmarkers.h  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace knihoven jazyka C++](../profiling/cpp-library-reference.md)



