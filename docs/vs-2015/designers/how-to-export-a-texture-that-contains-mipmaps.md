---
title: 'Postupy: Export textury obsahující mipmapy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 55418f40f57e2279100fbb1c9ba4d12fae83a19c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664448"
---
# <a name="how-to-export-a-texture-that-contains-mipmaps"></a>Postupy: Export textury obsahující mipmapy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kanál obsahu obrázku může vygenerovat mipmapy ze zdrojového obrázku jako součást fáze sestavení vašeho projektu. Pokud nepotřebujete určit obsah obrázku na každé úrovni MIP ručně, protože při vytváření mipmapy při sestavování nebudete muset mipmap obsah zajímat a eliminují se náklady na výkon při generování mipmapy v době běhu.

 Tento dokument znázorňuje tyto aktivity:

- Konfigurace zdrojového obrázku, který má být zpracován kanálem obsahu obrázku.

- Konfigurace kanálu obsahu obrázku tak, aby generoval mipmapy.

## <a name="exporting-mipmaps"></a>Export mipmapy
 Mipmapping poskytuje pro texturované plochy v 3D hře nebo aplikaci automatickou úroveň podrobností na obrazovce. Zlepšuje výkon při vykreslování hry nebo aplikace pomocí předběžného zpracování ukázkových verzí textury, aby celá textura nemusela být pokaždé vzorkování pokaždé, když je vzorkovaná.

#### <a name="to-export-a-texture-that-has-mipmaps"></a>Export textury, která má mipmapy

1. Začněte základní texturou. Načtěte existující soubor obrázku nebo ho vytvořte tak, jak je popsáno v tématu [Postupy: Vytvoření základní textury](../designers/how-to-create-a-basic-texture.md). Pro podporu mipmapy určete texturu, která má šířku a výšku, které mají stejnou mocninu dvou velikostí, například 64 × 64, 256x256 nebo 512x512.

2. Nakonfigurujte soubor textury, který jste právě vytvořili, aby byl zpracován kanálem obsahu obrázku. V **Průzkumník řešení**otevřete místní nabídku pro soubor textury, který jste právě vytvořili, a pak zvolte **vlastnosti**. Na stránce **Vlastnosti konfigurace**, **Obecné** nastavte vlastnost **typ položky na položku** **kanál obsahu obrázku**. Ujistěte se, že vlastnost **Content** je nastavena na **hodnotu Ano** a možnost **vyloučit ze sestavení** je nastavena na hodnotu **ne**, a poté klikněte na tlačítko **použít** . Zobrazí se stránka vlastností konfigurace **kanálu obsahu obrázku** .

3. Nakonfigurujte kanál obsahu obrázku tak, aby generoval mipmapy. Na stránce **Vlastnosti konfigurace**, **kanál obsahu obrázku**, **Obecné** nastavte vlastnost **Generovat MIPS** na **Ano (/generatemips)** .

4. Klikněte na tlačítko **OK** .

   Při sestavování projektu kanál obsahu obrazu převede zdrojový obraz z pracovního formátu na výstupní formát, který jste zadali, včetně úrovní MIP, a výsledek se zkopíruje do výstupního adresáře projektu.
