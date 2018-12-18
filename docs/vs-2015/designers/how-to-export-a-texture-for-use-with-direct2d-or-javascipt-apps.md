---
title: 'Postupy: Export textury pro použití s rozhraním Direct2D nebo aplikacemi | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 241c25fe-764e-4e1b-ad32-b1377dcbb605
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e2b08760e567f6e000e191703695ee0703da7215
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812137"
---
# <a name="how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps"></a>Postupy: Export textury pro použití s rozhraním Direct2D nebo aplikacemi JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kanál s obsahem obrazu může generovat textury, které jsou kompatibilní s Direct2D interní konvencí vykreslování. Textury tohoto druhu jsou vhodné pro použití v aplikacích, které používají rozhraní Direct2D a v aplikacích Windows Store, které jsou vytvořené pomocí jazyka JavaScript.  
  
 Tento dokument vysvětluje tyto činnosti:  
  
-   Konfigurace zdrojového obrazu pro zpracování obsahu kanálu obrázku.  
  
-   Konfigurace obsahu kanálu obrázku ke generování textur, který vám pomůže v aplikaci Direct2D nebo JavaScript.  
  
    -   Vygenerujte soubor komprimovanými .dds.  
  
    -   Generoval vynásobený kanál alfa.  
  
    -   Zakážete generování mipmap.  
  
## <a name="rendering-conventions-in-direct2d"></a>Vykreslování konvence v Direct2D  
 Textury, které se používají v souvislosti s Direct2D musí splňovat tyto vnitřní konvence Direct2D vykreslování:  
  
-   Direct2D implementuje průhlednost a průsvitnost pomocí předem vynásobené hodnoty alfa. Textury použité v rámci Direct2D musí obsahovat předem vynásobenou hodnotu alpha, i když textury nepoužívají průhlednost nebo průsvitnost. Další informace o přednásobeném kanálu alfa naleznete v tématu [postupy: Export textury s Přednásobeným alfa](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md).  
  
-   Textura musí být poskytována ve formátu .dds pomocí jednoho z těchto formátů komprese bloku:  
  
    -   Komprese BC1_UNORM  
  
    -   BC2_UNORM komprese  
  
    -   BC3_UNORM komprese  
  
-   Mipmapy nejsou podporovány.  
  
#### <a name="to-create-a-texture-thats-compatible-with-direct2d-rendering-conventions"></a>Vytvoření textury, který je kompatibilní s konvencemi vykreslování Direct2D  
  
1. Začněte základní texturou. Načtěte stávající obrazový nebo vytvořte novou, jak je popsáno v [postupy: vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Na podporu blokové komprese ve formátu .dds, určete texturu, která má šířku a výšku, které jsou násobky čtyř, velikost, například 100 x 100, 128 x 128 nebo 256 x 192. Protože není podporován mipmapping, textura nemá být čtvercová a nemá být mocninou čísla 2 velikosti.  
  
2. Nakonfigurujte soubor textury tak, aby byl zpracován kanálem obsahu obrázku. V **Průzkumníka řešení**, otevřete místní nabídku pro soubor textury, který jste právě vytvořili a klikněte na tlačítko **vlastnosti**. Na **vlastnosti konfigurace**, **Obecné** nastavte **typ položky** vlastnost **kanál obsahu obrazu**. Ujistěte se, že **obsahu** je nastavena na **Ano** a **vyloučit ze sestavení** je nastavena na **ne**a klikněte na tlačítko  **Použít** tlačítko. **Kanál obsahu obrazu** se zobrazí stránka pro konfiguraci vlastností.  
  
3. Nastavte formátu výstupu do jednoho z formátů komprimovanými. Na **vlastnosti konfigurace**, **kanál obsahu obrazu**, **Obecné** nastavte **komprimovat** vlastnost  **BC3_UNORM komprese (/ komprese: BC3_UNORM)**. Může zvolit některý z jiných formátů BC1, BC2 nebo BC3 formátů, v závislosti na vašich požadavcích. Direct2D nepodporuje aktuálně textury BC4, BC5, BC6 nebo BC7 textury. Další informace o různých formátech BC naleznete v tématu [bloková komprese (Direct3D 10)](http://msdn.microsoft.com/library/windows/desktop/bb694531.aspx).  
  
   > [!NOTE]
   >  Formát komprese, který je určen Určuje formát souboru, který je vytvořen kanál obsahu obrázku. To se liší od **formátu** vlastnost zdrojového obrázku v editoru obrázků, což určuje formát zdrojového souboru bitové kopie uloženého na disku – to znamená, *pracovního formátu*. Obvykle nechcete komprimovaný pracovní formát.  
  
4. Nakonfigurujte kanál obsahu obrázku vytvořit výstup, který používá předem vynásobené hodnoty alfa. Na **vlastnosti konfigurace**, **kanál obsahu obrazu**, **Obecné** nastavte **převést na formát přednásobené alfa** Vlastnost **Ano (/ generatepremultipliedalpha)**.  
  
5. Nakonfigurujte kanál obsahu obrázku tak, aby negeneroval mipmapy. Na **vlastnosti konfigurace**, **kanál obsahu obrazu**, **Obecné** nastavte **generovat Mips** vlastnost **Ne**.  
  
6. Zvolte **OK** tlačítko.  
  
   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali – převod zahrnuje generování předem vynásobených hodnot alfa – a výsledek je zkopírován do výstupního adresáře projektu.



