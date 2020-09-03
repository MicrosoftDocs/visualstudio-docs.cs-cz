---
title: StartTrackingContextWithRoot | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- StartTrackingContextWithRoot
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- StartTrackingContextWithRoot
ms.assetid: f6ef2b76-8035-4a14-8195-aa221c46ef48
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 68e80da01a0ab1ad59bbb5bdb06c92c1a11a8ac1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182325"
---
# <a name="starttrackingcontextwithroot"></a>StartTrackingContextWithRoot
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spustí sledovací kontext pomocí souboru odezvy určujícího kořenovou značku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI StartTrackingContextWithRoot(LPCTSTR intermediateDirectory, LPCTSTR taskName, LPCTSTR rootMarkerResponseFile);  
```  
  
#### <a name="parameters"></a>Parametry  
 pro `intermediateDirectory`  
 Adresář, do kterého má být uložen protokol sledování.  
  
 pro `taskName`  
 Identifikuje sledovací kontext. Tento název se používá k vytvoření názvu souboru protokolu.  
  
 pro `rootMarkerResponseFile`  
 Cesta k souboru odpovědí, který obsahuje kořenovou značku. Kořenový název slouží k seskupení všech sledování kontextu.  
  
## <a name="return-value"></a>Návratová hodnota  
 A [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) s [úspěch] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bitová sada, pokud byl kontext sledování vytvořen.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** Stopa. h  
  
## <a name="see-also"></a>Viz také  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
