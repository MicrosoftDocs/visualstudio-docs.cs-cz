---
title: 'Postupy: Export textury obsahující mipmapy | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 847655d04359fa795f878ea921e69b1b5cd16460
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49811734"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Postupy: Export textury obsahující mipmapy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kanál s obsahem obrazu může generovat mipmapy ze zdrojového obrazu jako část fáze se sestavením projektu. Když není potřeba ručně zadat obsah bitové kopie každé úrovně MIP, můžete využít k dosažení určitého efektu, generování mipmaps v okamžiku sestavení zajistí, že obsah mipmap nikdy stát--sync a eliminuje náklady na generování Mipmap v době běhu.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Konfigurace zdrojového obrazu pro zpracování obsahu kanálu obrázku.  
  
-   Konfigurace obsahu kanálu obrázku ke generování Mipmap.  
  
## <a name="exporting-mipmaps"></a>Exportování Mipmap  
 Mipmapping zajišťuje úroveň of-Detail automatické místo na obrazovce pro texturované povrchy u 3D her nebo aplikací. To zvyšuje rychlost vykreslování hry nebo aplikace předem výpočtem předvýpočtem zredukovaných verzí textur tak, aby celá textura nemá být zredukována pokaždé, když je vzorkována.  
  
#### <a name="to-export-a-texture-that-has-mipmaps"></a>Pro export textury obsahující mipmapy  
  
1. Začněte základní texturou. Načtěte stávající obrazový soubor nebo jej vytvořte podle pokynů v [postupy: vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Na podporu Mipmap určete texturu, která má šířku a výšku, které mají stejný výkon rozměry, například 64 x 64, 256 x 256 nebo 512 x 512.  
  
2. Nakonfigurujte soubor textury, které jste právě vytvořili, aby byl zpracován kanálem obsahu obrázku. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor textury, který jste právě vytvořili a klikněte na tlačítko **vlastnosti**. Na **vlastnosti konfigurace**, **Obecné** nastavte **typ položky** vlastnost **kanál obsahu obrazu**. Ujistěte se, že **obsahu** je nastavena na **Ano** a **vyloučit ze sestavení** je nastavena na **ne**a klikněte na tlačítko  **Použít** tlačítko. **Kanál obsahu obrazu** se zobrazí stránka pro konfiguraci vlastností.  
  
3. Nakonfigurujte kanál obsahu obrázku ke generování Mipmap. Na **vlastnosti konfigurace**, **kanál obsahu obrazu**, **Obecné** nastavte **generovat Mips** vlastnost **Ano (/ generatemips)**.  
  
4. Zvolte **OK** tlačítko.  
  
   Při vytváření projektu kanál obsahu obrázku tak převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali, včetně úrovní MIP a výsledek je zkopírován do výstupního adresáře projektu.



