---
title: 'Postupy: nastavení možností názvu datového souboru výkonu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 71ac053a24b3f765a58fc050ceec84115e1a4e3d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548392"
---
# <a name="how-to-set-performance-data-file-name-options"></a>Postupy: nastavení možností názvu datového souboru výkonu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ve výchozím nastavení uložíte soubor dat profilování (. vsp) pomocí následující syntaxe:  
  
 *Path\VSP-File\YYMMDD (N)* **. vsp**  
  
 Libovolný parametr pojmenování můžete změnit na stránce Obecné dialogového okna vlastnosti pro relaci výkonu.  
  
 **Požadavky**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
|Element syntax|Popis|  
|-|-|  
|*Cesta*|Adresář, který obsahuje sestavu. Výchozím umístěním je složka řešení nebo výchozí umístění pro projekty a řešení uživatele.|  
|*Soubor VSP*|Název souboru dat profilování. Výchozí název je název řešení nebo spustitelného souboru.|  
|*RRMMDD*|Časové razítko, které zobrazuje rok, měsíc a den, kdy se data profilace shromáždila.|  
|*N*|Pokud existuje více než jeden datový soubor profilování, přidá se k názvu souboru mezi závorky navýšené číslo.|  
  
### <a name="to-change-the-naming-syntax-of-the-profiling-data-files-of-a-performance-session"></a>Změna syntaxe názvů datových souborů profilování relace výkonu  
  
1. V **prohlížeč výkonu**klikněte pravým tlačítkem na název relace výkonu a pak klikněte na **vlastnosti**.  
  
2. Klikněte na **Obecné**.  
  
3. V části **Sestava**změňte kterékoli z následujících nastavení:  
  
    |Name|Popis|  
    |-|-|  
    |**Umístění sestavy**|Zadejte adresář, do kterého se mají ukládat soubory dat profilování.|  
    |**Název sestavy**|Zadejte základní název souborů.|  
    |**Automaticky přidávat nové sestavy do relace**|Zaškrtněte políčko, chcete-li automaticky přidat datový soubor do výkonnostní relace.|  
    |**Připojit přírůstkové číslo k vygenerovaným sestavám**|Zaškrtněte políčko, pokud chcete přidat přírůstkové číslo k názvu souboru, pokud existuje více než jeden soubor se stejným názvem. Zrušením zaškrtnutí políčka přepíšete existující soubor.|  
    |**Použít časové razítko pro číslo**|Zaškrtnutím políčka přidejte k názvu souboru dateStamp.|
