---
title: Řazení, filtrování a seskupování
description: Seznamte se s možnostmi, které jsou k dispozici v nabídce Možnosti řazení, filtrování a seskupování na panelu nástrojů Průzkumníka schémat XML.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 98ead8b2f0ddc7edc84449c3f80deeb7598fdfab
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99849759"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Řazení, filtrování a seskupování (Průzkumník schémat XML)

Toto téma popisuje možnosti, které jsou k dispozici v nabídce **Možnosti řazení, filtrování a seskupování** na panelu nástrojů **Průzkumníka schémat XML** .

## <a name="filter-options"></a>Možnosti filtru

K dispozici jsou následující možnosti filtru. Ve výchozím nastavení jsou vybrány možnosti **Zobrazit soubory oborů názvů** a **Zobrazit schéma** .

- **Zobrazit obory názvů**.

- **Zobrazit soubory schématu**.

- **Zobrazit kompozice (Sequence/Choice/All)**.

## <a name="sorting-options"></a>Možnosti řazení

K dispozici jsou následující možnosti řazení. Výchozí hodnota je **Sort podle typu**. Možnosti **řazení podle** možností se nevztahují na soubory a obory názvů.

- **Seřadit podle typu**

- **Seřadit podle názvu**

- **Pořadí dokumentů**.

### <a name="sort-by-type"></a>Seřadit podle typu

Když je vybrána možnost **Seřadit podle typu** , globální uzly jsou seřazeny v následujícím pořadí. Uzly jsou pak seřazené podle abecedy v rámci každé skupiny.

1. `import` sortiment.

2. `include` sortiment.

3. `redefine` sortiment.

4. `attribute` sortiment.

5. `attributeGroup` sortiment.

6. `complexType` sortiment.

7. `simpleType` sortiment.

8. `element` sortiment.

9. `group` sortiment.

### <a name="sort-by-name"></a>Seřadit podle názvu

Když je vybraná možnost **Seřadit podle názvu** , globální uzly se seřadí v následujícím pořadí:

1. `import` uzly (v abecedním pořadí oborů názvů).

2. `include` uzly (v abecedním pořadí `schemaLocation` atributů).

3. `redefine` uzly (v abecedním pořadí `schemaLocation` atributů).

4. Další globální uzly v abecedním pořadí.

### <a name="document-order"></a>Pořadí dokumentů

Možnost **pořadí dokumentů** je k dispozici, pokud je vybrána možnost **Zobrazit soubory schématu** . Pokud je vybráno **pořadí dokumentů** , globální uzly budou zobrazeny v pořadí, v jakém jsou uvedeny v souboru schématu.

## <a name="persisting-sortfilter-options"></a>Zachování možností řazení a filtrování

Možnosti řazení, filtrování a seskupování jsou uloženy v registru pro každého uživatele bez ohledu na to, jaké řešení nebo soubory byly otevřeny při změně nastavení.
