---
title: Pokyny k obsluze pro aplikace izolovaného prostředí | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159268"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Pokyny pro údržbu aplikací izolovaného prostředí
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když distribuujete aplikaci izolovaného prostředí sady Visual Studio, musíte být schopni poskytnout aktualizace softwaru pro vaši aplikaci po její instalaci. K tomu je nutné nainstalovat aplikaci pomocí souboru Instalační služby společnosti Microsoft (MSI). Tento typ instalace umožňuje, aby se aktualizace softwaru poskytované Microsoftem redistribuovány webovým stažením a spotřebou vašimi zákazníky bez vlastní intervence.  
  
## <a name="servicing-requirements"></a>Požadavky na údržbu  
 Můžete zajistit, aby instalace izolovaného prostředí mohla umožňovat aktualizace tím, že zajistí, že instalační program splňuje následující tři kritéria.  
  
### <a name="redistribute-by-using-an-msi"></a>Znovu distribuovat pomocí MSI  
 Chcete-li znovu distribuovat aplikaci, je nutné použít MSI, protože služba MSI zachovává identitu produktu a zajišťuje, že aplikace má fyzické umístění v klientském počítači. Slučovací moduly (soubory. msm) neposkytují taková ujištění a neměly by se používat.  
  
### <a name="accounting-for-custom-actions"></a>Monitorování účtů pro vlastní akce  
 Vlastní akce jsou nestandardní direktivy instalace v instalačním programu. Vlastní akce mění parametry, jako jsou například umístění souborů, nastavení registru, uživatelská nastavení nebo jiné položky instalace. Vlastní akce můžou manipulovat s daty v době instalace.  
  
 Když v instalačním programu použijete vlastní akce, musíte zajistit, aby každá vlastní akce při instalaci měla k dispozici odpovídající vlastní akce, která vrátí akci, když uživatel odinstaluje aplikaci. Pokud se instalační program nebude moci poskytnout odpovídající vlastní akci odinstalace, odebrání aplikace zůstane částečně nainstalováno.  
  
- Vlastní akce, která se spoléhá na konkrétní verzi souboru nebo hodnoty hash, selže, když aktualizace softwaru změní tyto verze nebo hodnoty hash. V takovém případě musí vaše vlastní akce aktualizovat tyto hodnoty ručně. K dalšímu problému dochází, pokud jsou verze souboru nebo hodnoty hash sdílené mezi verzemi produktu. Pokud je to možné, vyhněte se této závislosti.  
  
### <a name="accounting-for-shared-files"></a>Monitorování účtů pro sdílené soubory  
 Sdílené soubory mají stejné názvy a jsou nainstalovány do stejného umístění pomocí více produktů. Tyto produkty se můžou lišit v části verze, skladová jednotka (SKU) nebo obojí a produkty můžou existovat v daném počítači současně. Sdílené soubory ale vytvářejí problémy se zapínáním z několika důvodů:  
  
- Aktualizace sdílených souborů může způsobit problémy s kompatibilitou aplikací, protože aktualizace jedné aplikace může změnit verzi souboru používaného druhou aplikací, která se neaktualizovala. Instalační programy pro produkty, které sdílí soubory, se počítají jako odkazy na sdílené soubory. Proto odinstalace produktu nemá vliv na sdílené soubory, a to po snížení počtu nainstalovaných instancí.  
  
- Instalační program sady rychlých oprav (QFE) vrátí verze souborů do verzí produktů, které instalační program QFE zadalo. Tento proces potenciálně ukončí aplikaci, která aktualizovala aktualizovaný sdílený soubor.
