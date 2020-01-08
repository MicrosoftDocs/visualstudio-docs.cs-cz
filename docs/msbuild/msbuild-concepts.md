---
title: Koncepty nástroje MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aed8c97702989bdbdfd0f09c3cf99391c12fe9bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589276"
---
# <a name="msbuild-concepts"></a>Koncepty nástroje MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] poskytuje základní schéma XML, které lze použít k řízení způsobu sestavení softwaru sestavení Platform. Chcete-li určit komponenty v sestavení a jak mají být sestaveny, použijte tyto čtyři části nástroje MSBuild: vlastnosti, položky, úlohy a cíle.

## <a name="related-topics"></a>Příbuzná témata

| Název | Popis |
| - | - |
| [Vlastnosti nástroje MSBuild](../msbuild/msbuild-properties.md) | Zavádí vlastnosti a kolekce vlastností. Vlastnosti jsou páry klíč/hodnota, které lze použít ke konfiguraci sestavení. |
| [Položky nástroje MSBuild](../msbuild/msbuild-items.md) | Zavádí položky a kolekce položek. Položky jsou vstupy do systému sestavení a obvykle reprezentují soubory. |
| [Cíle nástroje MSBuild](../msbuild/msbuild-targets.md) | Vysvětluje, jak seskupit úkoly společně v určitém pořadí a povolit části procesu sestavení, které mají být volány v příkazovém řádku. |
| [Úlohy nástroje MSBuild](../msbuild/msbuild-tasks.md) | Ukazuje, jak vytvořit jednotku spustitelného kódu, který lze použít [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] k provádění atomických operací sestavení. |
| [Porovnávání vlastností a položek](../msbuild/comparing-properties-and-items.md) | Porovná vlastnosti a položky nástroje MSBuild. Oba se používají k předávání informací do úkolů, vyhodnocení podmínek a ukládání hodnot, na které lze odkazovat v rámci souboru projektu. |
| [Speciální znaky nástroje MSBuild](../msbuild/msbuild-special-characters.md) | Vysvětluje, jak Escape některé znaky, které [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezervují pro speciální použití v konkrétních kontextech. |
| [Návod: vytvoření souboru projektu MSBuild od začátku](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Ukazuje, jak vytvořit soubor základního projektu přírůstkově pomocí pouze textového editoru. |
| [Návod: Použití nástroje MSBuild](../msbuild/walkthrough-using-msbuild.md) | Zavádí stavební kameny nástroje MSBuild a ukazuje, jak psát, manipulovat a ladit projekty MSBuild bez zavření integrovaného vývojového prostředí (IDE) sady Visual Studio. |
| [Referenční dokumentace nástroje MSBuild](../msbuild/msbuild-reference.md) | Odkazuje na dokumenty, které obsahují referenční informace. |
| [MSBuild](../msbuild/msbuild.md) | Zobrazí přehled schématu XML pro soubor projektu a ukazuje, jak ovládací prvky řídí procesy, které sestavují software. |
