---
title: Vytváření řetězců filtru pro návrháře tabulky | Microsoft Docs
description: Sestavování řetězců filtru pro návrháře tabulky
author: ghogen
manager: jillfra
assetId: a1a10ea1-687a-4ee1-a952-6b24c2fe1a22
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/18/2016
ms.author: ghogen
ms.openlocfilehash: c76113f014d8be3bd706ef02ec1135a84cbcae82
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75849963"
---
# <a name="constructing-filter-strings-for-the-table-designer"></a>Vytváření filtračních řetězců pro Návrháře tabulky
## <a name="overview"></a>Přehled
Chcete-li filtrovat data v tabulce Azure, která je zobrazena v **Návrháři tabulky**aplikace Visual Studio, sestavíte řetězec filtru a zadáte ho do pole Filter. Syntaxe řetězce filtru je definována WCF Data Services a je podobná klauzuli WHERE jazyka SQL, ale je odeslána do Table service prostřednictvím požadavku HTTP. **Návrhář tabulky** zpracovává správné kódování, takže Chcete-li filtrovat podle požadované hodnoty vlastnosti, je nutné zadat pouze název vlastnosti, operátor porovnání, hodnotu kritéria a volitelně logický operátor v poli Filter. Nemusíte zahrnovat možnost dotazu $filter, protože byste vytvořili adresu URL pro dotazování tabulky prostřednictvím [služby Storage REST API Reference](https://msdn.microsoft.com/library/dd179355.aspx).

WCF Data Services jsou založené na protokolu OData ( [Open Data Protocol](https://www.odata.org/) ). Podrobnosti o možnosti dotazu systému filtru ( **$Filter**) najdete v tématu specifikace pro [konvenci identifikátorů URI OData](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).

## <a name="comparison-operators"></a>Operátory porovnání
Následující logické operátory jsou podporovány pro všechny typy vlastností:

| Logický operátor | Popis | Příklad řetězce filtru |
| --- | --- | --- |
| přepínače |Rovno |Město EQ – Redmond |
| gt |Větší než |Cena gt 20 |
| GE |Větší nebo rovno |Cena GE 10 |
| lt |Menší než |Cena lt 20 |
| osoby |Menší nebo rovno |Cena Le 100 |
| d |Nerovná se |Město ne Londýn |
| and |A |Cena Le 200 a cena gt 3,5 |
| nebo |Nebo |Cena Le 3,5 nebo cena gt 200 |
| not |Not |není k dispozici |

Při sestavování řetězce filtru jsou důležité následující pravidla:

* Pomocí logických operátorů Porovnejte vlastnost s hodnotou. Všimněte si, že není možné porovnat vlastnost s dynamickou hodnotou; jedna strana výrazu musí být konstanta.
* Ve všech částech řetězce filtru se rozlišují malá a velká písmena.
* Hodnota konstanty musí být stejného datového typu jako vlastnost, aby filtr vrátil platné výsledky. Další informace o podporovaných typech vlastností najdete v tématu [Vysvětlení datového modelu služby Table Service](https://msdn.microsoft.com/library/dd179338.aspx).

## <a name="filtering-on-string-properties"></a>Filtrování vlastností řetězce
Při filtrování vlastností řetězce uzavřete řetězcovou konstantu do jednoduchých uvozovek.

Následující příklad filtruje vlastnosti **PartitionKey** a **RowKey** ; do řetězce filtru je také možné přidat další neklíčové vlastnosti:

```
PartitionKey eq 'Partition1' and RowKey eq '00001'
```

Každý výraz filtru můžete uzavřít do závorek, přestože není vyžadován:

```
(PartitionKey eq 'Partition1') and (RowKey eq '00001')
```

Všimněte si, že Table service nepodporuje dotazy se zástupnými znaky a nejsou podporovány v Návrháři tabulky. Porovnávání předpon lze však použít pomocí operátorů porovnání na požadované předpony. Následující příklad vrátí entity s vlastností LastName začínající písmenem "A":

```
LastName ge 'A' and LastName lt 'B'
```

## <a name="filtering-on-numeric-properties"></a>Filtrování podle číselných vlastností
Chcete-li filtrovat celé číslo nebo číslo s plovoucí desetinnou čárkou, zadejte číslo bez uvozovek.

Tento příklad vrátí všechny entity s vlastností věk, jejíž hodnota je větší než 30:

```
Age gt 30
```

Tento příklad vrátí všechny entity s vlastností AmountDue, jejíž hodnota je menší než nebo rovna 100,25:

```
AmountDue le 100.25
```

## <a name="filtering-on-boolean-properties"></a>Filtrování u logických vlastností
Chcete-li filtrovat podle logické hodnoty, zadejte **hodnotu true** nebo **false** bez uvozovek.

Následující příklad vrátí všechny entity, u kterých je vlastnost IsActive nastavena na **hodnotu true**:

```
IsActive eq true
```

Tento výraz filtru můžete také napsat bez logického operátoru. V následujícím příkladu vrátí Table service také všechny entity, kde je **vlastnost IsActive pravdivá**:

```
IsActive
```

Chcete-li vrátit všechny entity, kde má vlastnost IsActive hodnotu false, můžete použít operátor NOT:

```
not IsActive
```

## <a name="filtering-on-datetime-properties"></a>Filtrování podle vlastností data a času
Chcete-li filtrovat hodnotu DateTime, zadejte klíčové slovo **DateTime** následovaný konstantou data a času v jednoduchých uvozovkách. Konstanta data a času musí být v kombinovaném formátu UTC, jak je popsáno v části [formátování hodnot vlastnosti DateTime](https://msdn.microsoft.com/library/azure/dd894027.aspx).

Následující příklad vrátí entity, kde je vlastnost CustomerSince rovna 10. července 2008:

```
CustomerSince eq datetime'2008-07-10T00:00:00Z'
```
