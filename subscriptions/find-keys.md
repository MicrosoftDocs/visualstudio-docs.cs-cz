---
title: Vyhledání a nárokování kódů Product Key v předplatných sady Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: cabuschl
ms.assetid: da8df006-4896-4ff9-b487-698d78deabc3
ms.date: 07/30/2020
ms.topic: conceptual
description: Naučte se najít, vyžádat a exportovat kódy Product Key v předplatných sady Visual Studio.
ms.openlocfilehash: e9be61db1f72684dcff12d015ec5180607b41977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250728"
---
# <a name="finding-and-claiming-product-keys-in-visual-studio-subscriptions"></a>Vyhledání a nárokování kódů Product Key v předplatných sady Visual Studio
Tento článek vysvětluje, jak najít, vyžádat a exportovat kódy Product Key z https://my.visualstudio.com/productkeys .  Další informace o aktivaci produktu pomocí klíče, maloobchodních a multilicenčních verzí klíčů a denních limitů deklarací identity pro klíč produktu najdete na stránce [Přehled kódů Product](product-keys.md)Key.

## <a name="locating-and-claiming-product-keys"></a>Vyhledání a nárokování kódů Product Key
Abyste mohli zobrazit kódy Product Key, musíte být přihlášení k vašemu předplatnému sady Visual Studio. Jednotlivé kódy Product Key najdete tak, že na stránce [soubory ke stažení](https://my.visualstudio.com/downloads) vyberete odkaz modrého **klíče** pro určitý produkt, jak je znázorněno níže.  Všechny klíče jsou také k dispozici ve agregované na stránce [kódy Product Key](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) . Pokud pro jeden produkt existuje více klíčů, zobrazí se ve sloupci poznámky ke stažení poznámky, které vám pomůžou určit, který klíč se má použít.
> [!div class="mx-imgBorder"]
> ![Získat klíč ze stránky soubory ke stažení](_img/product-keys/download-get-key.png "Na stránce informace vyberte získat klíč pro jakékoli stažení a získejte pro daný produkt klíč.")

Některé produkty zabalí více edicí produktu do jediného stažení. V těchto případech se zadaným produktovým klíčem určí, která edice produktu je nainstalovaná.
Některé klíče jsou k dispozici automaticky, například "statické" klíče, které můžete použít tolikrát, kolikrát je potřeba, protože aktivace není nutná. Další klíče musí být vyžádány tak, že vyberete odkaz **získat klíč** pro daný produkt.

V závislosti na produktu je k dispozici celá řada typů klíčů.

### <a name="product-key-types"></a>Typy kódu Product Key

|    Typ klíče           |    Popis                                                                                                                                                                                                           |
|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Neuvedeno                    |    K instalaci tohoto produktu není nutný žádný klíč.                                                       |
|    Retail                     |    Maloobchodní klíče umožňují více aktivací a používají se pro maloobchodní buildy produktu. V mnoha případech jsou povolené 10 aktivací na klíč, i když ve stejném počítači jsou často víc.                                                       |
|    Vícenásobná aktivace        |    Klíč k vícenásobné aktivaci (MAK) umožňuje aktivovat více instalací produktu se stejným klíčem. MAKs se běžně používají s multilicenčními verzemi produktů. Pro každé předplatné je obvykle k dispozici pouze jeden klíč MAK.    |
|    Statický aktivační klíč    |    Pro produkty, které nevyžadují aktivaci, jsou k dispozici statické aktivační klíče. Dají se použít pro libovolný počet instalací.                                                                                                                  |
|    Vlastní klíč                 |    Vlastní klíče poskytují speciální akce nebo informace pro aktivaci nebo instalaci produktu.                                                                                                                                                                |
|    VA 1,0                     |    Jedná se o více aktivačních klíčů, podobně jako u klíče k vícenásobné aktivaci.                                                                                                                                                                                                 |
|    Klíč OEM                    |    Jedná se o původní klíče výrobců zařízení, které umožňují více aktivací.                                                                                                                                                                       |
|    DreamSpark maloobchodní klíč    |    Tyto maloobchodní klíče jsou pro DreamSpark a umožňují jednu aktivaci. DreamSpark maloobchodní klíče se vystavují v dávkách a jsou primárně určené pro studenty.                                                                                     |
|    Klíč testovacího prostředí DreamSpark         |    Tyto klíče testovacího prostředí se používají pro programy DreamSpark a umožňují více aktivací. Klíče testovacího prostředí DreamSpark jsou určené pro použití ve scénářích počítačové laboratoře.                                                                                       |
|    Klíč MAK DreamSpark         |    Jedná se o klíče MAK pro zákazníky programu DreamSpark.                                                                                                                                                                                                  |
|

Můžete si vyžádat klíč ze stránky pro stahování pro daný produkt, nebo můžete vyhledat klíč, který potřebujete, na stránce [kódy Product Key](https://my.visualstudio.com/productkeys) .

### <a name="claiming-product-keys"></a>Deklarace kódů Product Key
Pouze předplatitelé s aktivním předplatným můžou stahovat produkty a kódy Product Key pro nárok.  Přihlášené klíče můžete exportovat ze stránky [Product Key](https://my.visualstudio.com/productkeys) , pokud je vaše předplatné aktivní.

Deklarace kódu Product Key:
1. Přihlaste se k předplatnému sady Visual Studio.  Abyste mohli stahovat produkty nebo kódy Product Key, musíte být přihlášení.
2. Vyberte kartu [kódy Product Key](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) .
3. Kódy Product Key jsou seřazené abecedně podle názvu produktu.  Můžete se buď posunout dolů na název požadovaného produktu, nebo ho vyhledat pomocí panelu hledání v horní části stránky.
> [!div class="mx-imgBorder"]
> ![Vyhledat kód Product Key](_img/product-keys/search-keys.png "Posuňte se na požadovaný produkt, nebo pomocí vyhledávacího pole rychle vyhledejte libovolný produkt.")
   
V tomto příkladu jsme použili panel hledání k vyhledání kódu Product Key pro Visual Studio Enterprise 2019.
Jak vidíte, obsahuje několik uvedených verzí.  Jeden klíč, který již byl požadován pro Visual Studio Enterprise 2019 verze 16,0 a 16,1.  Pro obě verze jsou stále k dispozici další klíče různých typů. Všimněte si, že si můžete zaznamenat stručnou poznámku o deklarovaných klíčích ve sloupci **poznámky** .  Tuto možnost můžete použít spolu s datem ve sloupci **požadováno** k udržení přehledu o klíčích, které jste si vyžádali.  Můžete například vytvořit poznámky při aktivaci instalace produktu pomocí klíče.

### <a name="exporting-your-claimed-keys"></a>Export požadovaných klíčů
Můžete exportovat seznam všech požadovaných klíčů a také velký výběr statických a dalších klíčů, které jsou automaticky označeny jako "tvrzeno".

> [!IMPORTANT]
> Pokud platnost vašeho předplatného vyprší, nebudete už moct žádat o nové klíče ani exportovat požadované klíče.

Pokud chcete exportovat klíče, jednoduše vyberte odkaz **exportovat všechny klíče** v pravém rohu stránky kódy Product Key.  Vytvoří se soubor. XML s názvem KeysExport.xml a budete mít možnost soubor otevřít nebo Uložit.  Soubor budete muset otevřít v aplikaci, která umí pracovat se soubory .xml.  Soubor můžete například otevřít jako sešit jen pro čtení v Excelu.

## <a name="see-also"></a>Viz také
- [Dokumentace k sadě Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentace ke službě Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentace k Azure](https://docs.microsoft.com/azure/)
- [Dokumentace k Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Další kroky
Až budete připraveni ke stažení softwaru a použití klíčů, navštivte https://my.visualstudio.com/downloads .  Další informace o stahování softwaru najdete v [přehledu stahování](download-software.md).