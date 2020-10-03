---
title: Podpora rozhraní DirectX 12 v aplikaci Visual Studio | Microsoft Docs
description: Uživatelům rozhraní DirectX 12 se doporučuje používat PIX v systému Windows, aby bylo možné plně využívat grafické ladění.
ms.date: 09/29/2020
ms.topic: conceptual
author: davidcongruili
ms.author: davidli1
manager: mluparu
ms.workload:
- multiple
ms.openlocfilehash: 9dbc52a0233abe467da4d41af0134663bc7cd9df
ms.sourcegitcommit: a1cb4e2025045c2ad79167645c4c0f33b94b1152
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2020
ms.locfileid: "91671395"
---
# <a name="directx-12-support-in-visual-studio"></a>Podpora rozhraní DirectX 12 v aplikaci Visual Studio

## <a name="directx-12-support"></a>Podpora rozhraní DirectX 12

Visual Studio Diagnostika grafiky nepodporuje hry DirectX 12. Pro grafické ladění s plnou podporou rozhraní DirectX 12 doporučuje Visual Studio používat *pix v systému Windows*. 

PIX v systému Windows je nástroj pro ladění a ladění výkonu se vzdálenými funkcemi. PIX v systému Windows nabízí sedm hlavních funkcí, které vyhovují vašim potřebám vašeho grafického ladění. Umožňuje ladit a analyzovat výkon vykreslování grafiky Direct3D 12 pomocí zachycení GPU. Seznamte se s výkonem a vlákny pro veškerou práci procesoru a GPU, kterou vaše hra provádí, s časováním zachycení. Identifikujte neefektivitu ve vzorcích vstupně-výstupních operací disku a rozložení balíčku pomocí zachycení souborů v/v.

Stiskněte svou cestu k grafickému ladění s [**pix ve Windows**](https://aka.ms/PIXonWindows).

[**Stáhněte si pix do Windows**](https://aka.ms/downloadPIX) nebo si [ **Prohlédněte dokumentaci**.](https://devblogs.microsoft.com/pix/documentation/)

## <a name="pix-on-windows"></a>PIX ve Windows

Funkce PIX ve Windows – sedm hlavních režimů provozu:
1. **GPU zachycuje** pro ladění a analýzu výkonu vykreslování grafiky Direct3D 12.
2. **Časování zaznamenává** informace o výkonu a vláknech všech prací procesoru a GPU prováděných hrou a ke sledování využití paměti GPU.
3. **Souhrn funkcí zachycuje** informace o tom, jak dlouho se jednotlivé funkce spouštějí a jak často jsou jednotlivé funkce volány.
4. **Graf volání zachycuje** trasování spuštění jedné funkce.
5. **Zachycení přidělení paměti** poskytují přehled o přidělení paměti provedené hrou.
6. **Zachycení v/v souborů** vám pomůžou identifikovat neefektivitu ve vzorcích/vstupně-výstupních operacích disku a rozložení balíčku.
7. **Monitorování systému** zobrazuje data čítače v reálném čase, když je hra spuštěná.

Podrobné informace o programu PIX ve Windows [ **najdete tady** .](https://www.youtube.com/playlist?list=PLeHvwXyqearWuPPxh6T03iwX-McPG5LkB)
