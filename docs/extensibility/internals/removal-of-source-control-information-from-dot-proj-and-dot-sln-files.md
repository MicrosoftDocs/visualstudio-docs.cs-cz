---
title: Odebrání informace o řízení zdroje z. Proj a. Sln – soubory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 695a4ccfc5da20bda25c78929488625c244959a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128984"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>Odebrání informace o řízení zdroje z. Proj a. Sln – soubory
Ve verzi 1.2 rozhraní API modulu Plugin zdroj ovládacího prvku SCC informace jsou uloženy v MSSCCPRJ. SCC soubor. Výhodou MSSCCPRJ. Soubor SCC je, že není zdroje informace SCC - řídí, jako je tomu v souborech .proj a .sln.  
  
## <a name="version-12-changes"></a>Změny verze 1.2  
 Informace o zdrojového kódu je v zdroj ovládacího prvku zásuvné moduly, které jsou založeny na zdroj ovládacího prvku Plug-in volání rozhraní API verze 1.1, uloženy v projektu (.proj) a soubory řešení (.sln). Informace o řízení zdrojového umístění databáze je zadána AuxPath a konkrétního umístění v rámci databáze je zadána ProjName. Toto chování může způsobit problémy po větve, rozvětvení nebo operace kopírování, protože ProjName by byla obvykle neplatný po kteroukoli z těchto operací.  
  
 V rozhraní API modulu Plugin ovládací prvek zdroj verze 1.1, rozhraní IDE používá ~ SAK soubory ke zjištění, jestli podporuje modul plug-in MSSCCPRJ. Metoda SCC ukládání informací o zdroj ovládacího prvku. Zdroj ovládacího prvku Plug-in API verze 1.2 poskytuje novou funkci pro podporu MSSCCPRJ zjišťování. SCC souboru bez použití ~ SAK souboru. Další informace najdete v tématu [odstranění ~ SAK soubory](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Viz také  
 [Co je nového v rozhraní API modulu plug-in správy zdrojového kódu ve verzi 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)