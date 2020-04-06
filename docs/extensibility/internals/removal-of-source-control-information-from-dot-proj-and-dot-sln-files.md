---
title: Odebrání informací o směřovacím systému ze souborů .proj a .sln
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba3085a7806bfb0556613d1fca1b94953dcdb0b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705591"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Odebrání informací o správě zdrojového kódu ze souborů .Proj a .Sln
Ve verzi 1.2 rozhraní plug-in source control jsou informace SCC uloženy v mssccprj. SCC. Výhodou MSSCCPRJ. SCC soubor je, že informace SCC není zdroj-řízené, stejně jako je v .proj a .sln soubory.

## <a name="version-12-changes"></a>Změny verze 1.2
 V modulech plug-in správy zdrojového kódu, které jsou založeny na rozhraní API plug-in správy zdrojového kódu verze 1.1, jsou informace o správě zdrojového kódu uloženy v souborech projektu (.proj) a řešení (.sln). Umístění databáze informací o ovládacím prvku zdroj je určeno AuxPath a konkrétní umístění v databázi je určeno ProjName. Toto chování může způsobit problémy po operaci větve, rozvětvení nebo kopírování, protože ProjName by obvykle neplatné po některé z těchto operací.

 V rozhraní API modulu plug-in správy zdrojového kódu verze 1.1 rozhraní IDE použilo soubory ~SAK ke zjištění, zda modul plug-in podporuje modul MSSCCPRJ. SCC metoda ukládání informací o směřování zdrojového kódu. Rozhraní Api modulu plug-in správy zdrojového kódu verze 1.2 poskytuje novou funkci pro detekci podpory pro MSSCCPRJ. SCC bez použití souboru ~SAK. Další informace naleznete [v tématu Odstranění souborů ~SAK](../../extensibility/internals/elimination-of-tilde-sak-files.md).

## <a name="see-also"></a>Viz také
- [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
