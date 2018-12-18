---
title: Pokyny pro obsluhu izolovaných aplikací prostředí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a795e5dc71183550e660f8ce7d67f1a41bddbcf4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51726781"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Pokyny pro údržbu aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při distribuci aplikace Visual Studio izolované prostředí musí být schopný poskytnout aktualizace softwaru pro vaši aplikaci, poté, co je nainstalována. Chcete-li to provést, musíte nainstalovat aplikace pomocí souboru Microsoft Installer (MSI). Tento typ instalace umožňuje aktualizace softwaru od Microsoftu znovu distribuovat pomocí webových stáhnout a používat vaši zákazníci bez zásahu vlastní.  
  
## <a name="servicing-requirements"></a>Požadavky na údržbu.  
 Můžete zajistit, že vaše instalace izolovaného prostředí můžete povolit aktualizace zajištěním, že instalační program splňuje následující kritéria tři.  
  
### <a name="redistribute-by-using-an-msi"></a>Znovu distribuovat pomocí MSI  
 Je nutné použít instalační služba MSI distribuovat aplikace, protože instalační služba MSI uchovává identity produktu a zajišťuje, že aplikace má fyzické umístění v klientském počítači. Slučovací moduly (soubory .msm) se nevztahuje Smlouva takové záruky a neměl by se používat.  
  
### <a name="accounting-for-custom-actions"></a>Monitorování účtů pro vlastní akce  
 Vlastní akce jsou nestandardní instalace direktivy v aplikaci Instalační služby. Vlastní akce změnit parametry, jako je například umístění souborů, nastavení registru, nastavení uživatele nebo jiné položky instalace. Vlastní akce mohou manipulovat s daty v době instalace.  
  
 Pokud používáte vlastní akce v instalačním programu, musíte zajistit, že každá vlastní akce, čas instalace musí mít odpovídající vlastní akce vrátit zpět akce, když uživatel odinstaluje aplikaci. Pokud váš program instalace se nezdaří kvůli odpovídající vlastní akce odinstalace, odebírá se vaše aplikace bude necháte částečně nainstalováno.  
  
-   Vlastní akce, která závisí na konkrétní verzi souboru nebo hodnoty hash hodnoty se nezdaří, pokud změnit tyto verze aktualizací softwaru nebo hodnoty hash. Vlastní akce v tomto případě musíte ručně aktualizovat tyto hodnoty. Další problém nastane, pokud verze souboru nebo hodnoty hash hodnoty jsou sdílené mezi verzemi tohoto produktu. Vyhněte se tato závislost, kdykoli je to možné.  
  
### <a name="accounting-for-shared-files"></a>Monitorování účtů pro sdílené soubory  
 Sdílené soubory mají stejné názvy a jsou nainstalovány do stejného umístění ve více produktů. Tyto produkty se může lišit v verze nebo akcie udržování jednotky (SKU) a produktů mohou existovat vedle sebe v daném počítači. Sdílené soubory však vytvořit údržby problémy z několika důvodů:  
  
-   Aktualizace sdílených souborů může způsobit problémy s kompatibilitou aplikace, protože aktualizaci jedné aplikace může změnit verzi souboru používaný druhou aplikaci, která ještě není aktualizovaný. Instalační programy pro produkty, které sdílejí soubory počet odkazů na sdílené soubory. Proto se odinstalace produktu nemá vliv na sdílené soubory nad rámec dekrementace počet nainstalovaných instancí.  
  
-   Instalační program Quick Fix Engineering (QFE) se vrátí verze souborů na verze produktů, které obsluhují QFE Instalační služby. Přeruší potenciálně aplikaci, která má doručit aktualizované sdílený soubor.

