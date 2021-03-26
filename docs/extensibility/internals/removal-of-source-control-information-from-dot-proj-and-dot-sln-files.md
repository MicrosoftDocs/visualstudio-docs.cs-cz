---
title: Odebrání informací o správě zdrojového kódu ze souborů. proj a. sln
description: V rozhraní API modulu plug-in správy zdrojových kódů jsou informace SCC uloženy v MSSCCPRJ. Soubor SCC namísto projektu a souborů řešení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5fd4b4f12ab819903408d4d895773664e892b3ac
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069384"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Odebrání informací o správě zdrojového kódu ze souborů. proj a. sln

Ve verzi 1,2 rozhraní API modulu plug-in správy zdrojových kódů jsou informace SCC uloženy v MSSCCPRJ. Soubor SCC Výhodou MSSCCPRJ. Soubor SCC je, že informace SCC nejsou řízené zdrojem, stejně jako v souborech. proj a. sln.

## <a name="version-12-changes"></a>Změny verze 1,2

 V modulech plug-in správy zdrojového kódu, které jsou založeny na rozhraní API modulu plug-in správy zdrojového kódu verze 1,1, jsou informace o správě zdrojového kódu uloženy v souborech projektu (. proj) a řešení (. sln). Umístění databáze informací o správě zdrojového kódu je určeno AuxPath a konkrétní umístění v rámci databáze je určeno parametrem ProjName. Toto chování může způsobit problémy po větvích, rozvětvení nebo kopírování, protože ProjName by obvykle bylo po kterékoli z těchto operací neplatné.

 V rozhraní API modulu plug-in správy zdrojového kódu verze 1,1 rozhraní IDE používá soubory ~ SAK k detekci, zda modul plug-in podporoval rozhraní MSSCCPRJ. Metoda SCC ukládání informací o správě zdrojového kódu. Rozhraní API pro modul plug-in správy zdrojového kódu verze 1,2 poskytuje novou možnost zjišťování podpory pro MSSCCPRJ. SCC soubor bez použití souboru ~ SAK. Další informace najdete v tématu [odstranění souborů ~ sak](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Viz také

- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
