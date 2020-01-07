---
title: Řazení, filtrování a seskupování v Průzkumníkovi schémat XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd288171cd8713e6b403f71a4eee6ba09d3f6ea9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592513"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Řazení, filtrování a seskupování (Průzkumník schémat XML)

Toto téma popisuje možnosti, které jsou k dispozici v nabídce **Možnosti řazení, filtrování a seskupování** na panelu nástrojů **Průzkumníka schémat XML** .

## <a name="filter-options"></a>Možnosti filtru

K dispozici jsou následující možnosti filtru. Ve výchozím nastavení jsou vybrány možnosti **Zobrazit soubory oborů názvů** a **Zobrazit schéma** .

- **Zobrazit obory názvů**.

- **Zobrazit soubory schématu**.

- **Zobrazit kompozice (Sequence/Choice/All)** .

## <a name="sorting-options"></a>Možnosti řazení

K dispozici jsou následující možnosti řazení. Výchozí hodnota je **Sort podle typu**. Možnosti **řazení podle** možností se nevztahují na soubory a obory názvů.

- **Seřadit podle typu**

- **Seřadit podle názvu**

- **Pořadí dokumentů**.

### <a name="sort-by-type"></a>Seřadit podle typu

Když je vybrána možnost **Seřadit podle typu** , globální uzly jsou seřazeny v následujícím pořadí. Uzly jsou pak seřazené podle abecedy v rámci každé skupiny.

1. uzly `import`.

2. uzly `include`.

3. uzly `redefine`.

4. uzly `attribute`.

5. uzly `attributeGroup`.

6. uzly `complexType`.

7. uzly `simpleType`.

8. uzly `element`.

9. uzly `group`.

### <a name="sort-by-name"></a>Seřadit podle názvu

Když je vybraná možnost **Seřadit podle názvu** , globální uzly se seřadí v následujícím pořadí:

1. uzly `import` (v abecedním pořadí oborů názvů).

2. uzly `include` (v abecedním pořadí atributů `schemaLocation`).

3. uzly `redefine` (v abecedním pořadí atributů `schemaLocation`).

4. Další globální uzly v abecedním pořadí.

### <a name="document-order"></a>Pořadí dokumentů

Možnost **pořadí dokumentů** je k dispozici, pokud je vybrána možnost **Zobrazit soubory schématu** . Pokud je vybráno **pořadí dokumentů** , globální uzly budou zobrazeny v pořadí, v jakém jsou uvedeny v souboru schématu.

## <a name="persisting-sortfilter-options"></a>Zachování možností řazení a filtrování

Možnosti řazení, filtrování a seskupování jsou uloženy v registru pro každého uživatele bez ohledu na to, jaké řešení nebo soubory byly otevřeny při změně nastavení.
