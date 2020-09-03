---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
api_name:
- WriteContextTLogs
api_location:
- filetracker.dll
api_type:
- COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bba9c5b46aa01cddca4de5c8e1347b540999289
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156451"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapisuje soubory protokolů pro aktuální kontext.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametry  
 pro `intermediateDirectory`  
 Adresář, do kterého má být uložen protokol sledování.  
  
 pro `tlogRootName`  
 Název kořenového souboru protokolu  
  
## <a name="return-value"></a>Návratová hodnota  
 A [HRESULT] (<!-- TODO: review code entity reference <xref:assetId:///HRESULT?qualifyHint=False&amp;autoUpgrade=True>  -->) s [úspěch] (<!-- TODO: review code entity reference <xref:assetId:///SUCCEEDED?qualifyHint=False&amp;autoUpgrade=True>  -->) bitová sada, pokud byl kontext sledování vytvořen.  
  
## <a name="requirements"></a>Požadavky  
 **Hlavička:** Stopa. h  
  
## <a name="see-also"></a>Viz také  
 [WriteAllTLogs](../msbuild/writealltlogs.md)
