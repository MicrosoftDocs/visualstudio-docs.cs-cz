---
title: Koncepty nástroje MSBuild | Microsoft Docs
description: Naučte se určovat komponenty a procesy sestavení pomocí vlastností, položek, úkolů a cílů nástroje MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f9b83c83f2826334b5f43d387a2d7c6941ba4d91
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919170"
---
# <a name="msbuild-concepts"></a>Koncepty nástroje MSBuild

Nástroj MSBuild poskytuje základní schéma XML, které lze použít k určení způsobu, jakým sestavovací platforma sestaví software. Chcete-li určit komponenty v sestavení a jak mají být sestaveny, použijte tyto čtyři části nástroje MSBuild: vlastnosti, položky, úlohy a cíle.

## <a name="related-topics"></a>Související témata

| Nadpis | Popis |
| - | - |
| [vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md) | Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč/hodnota, které lze použít ke konfiguraci sestavení. |
| [Položky nástroje MSBuild](../msbuild/msbuild-items.md) | Zavádí položky a kolekce položek. Položky jsou vstupy do systému sestavení a obvykle reprezentují soubory. |
| [Cíle nástroje MSBuild](../msbuild/msbuild-targets.md) | Vysvětluje, jak seskupit úkoly společně v určitém pořadí a povolit části procesu sestavení, které mají být volány v příkazovém řádku. |
| [úlohy nástroje MSBuild](../msbuild/msbuild-tasks.md) | Ukazuje, jak vytvořit jednotku spustitelného kódu, který může nástroj MSBuild použít k provedení atomických operací sestavení. |
| [Porovnávání vlastností a položek](../msbuild/comparing-properties-and-items.md) | Porovná vlastnosti a položky nástroje MSBuild. Oba se používají k předávání informací do úkolů, vyhodnocení podmínek a ukládání hodnot, na které lze odkazovat v rámci souboru projektu. |
| [Speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md) | Vysvětluje, jak řídicí znaky vyhradit pro speciální použití v konkrétních kontextech nástroje MSBuild. |
| [Návod: Vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru. |
| [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md) | Zavádí stavební kameny nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild bez zavření integrovaného vývojového prostředí (IDE) sady Visual Studio. |
| [Jak MSBuild sestavuje projekty](build-process-overview.md) | Popisuje interní proces sestavení používaný v rámci nástroje MSBuild. |
| [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md) | Odkazuje na dokumenty, které obsahují referenční informace. |
| [MSBuild](../msbuild/msbuild.md) | Zobrazí přehled schématu XML pro soubor projektu a ukazuje, jak ovládací prvky řídí procesy, které sestavují software. |
