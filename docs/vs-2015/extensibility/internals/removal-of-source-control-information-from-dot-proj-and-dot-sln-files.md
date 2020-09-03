---
title: Odebrání informací o správě zdrojového kódu z. PROJ a. Soubory sln | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199378"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Odebrání informací o správě zdrojového kódu ze souborů .Proj a .Sln
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ve verzi 1,2 rozhraní API modulu plug-in správy zdrojových kódů jsou informace SCC uloženy v MSSCCPRJ. Soubor SCC Výhodou MSSCCPRJ. Soubor SCC je, že informace SCC nejsou řízené zdrojem, stejně jako v souborech. proj a. sln.  
  
## <a name="version-12-changes"></a>Změny verze 1,2  
 V modulech plug-in správy zdrojového kódu, které jsou založeny na rozhraní API modulu plug-in správy zdrojového kódu verze 1,1, jsou informace o správě zdrojového kódu uloženy v souborech projektu (. proj) a řešení (. sln). Umístění databáze informací o správě zdrojového kódu je určeno AuxPath a konkrétní umístění v rámci databáze je určeno parametrem ProjName. Toto chování může způsobit problémy po větvích, rozvětvení nebo kopírování, protože ProjName by obvykle bylo po kterékoli z těchto operací neplatné.  
  
 V rozhraní API modulu plug-in správy zdrojového kódu verze 1,1 rozhraní IDE používá soubory ~ SAK k detekci, zda modul plug-in podporoval rozhraní MSSCCPRJ. Metoda SCC ukládání informací o správě zdrojového kódu. Rozhraní API pro modul plug-in správy zdrojového kódu verze 1,2 poskytuje novou možnost zjišťování podpory pro MSSCCPRJ. SCC soubor bez použití souboru ~ SAK. Další informace najdete v tématu [odstranění souborů ~ sak](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
