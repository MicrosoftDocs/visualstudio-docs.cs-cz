---
title: Zahrnutí datového souboru do aplikace ClickOnce
description: Naučte se, jak do aplikace ClickOnce přidat datový soubor libovolného typu, který se uloží do datového adresáře na místním disku cílového počítače.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, data
- deploying applications [ClickOnce], data files
- data access, ClickOnce applications
ms.assetid: 89ee46ef-bc8c-4ab0-a2ac-1220f9da06fc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb9e346022871a3aa25363aa717f1bf15a3d42a6
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349942"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Postupy: zahrnutí datového souboru do aplikace ClickOnce
Každá [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace, kterou nainstalujete, je přiřazená datový adresář na místním disku cílového počítače, kde aplikace může spravovat svoje vlastní data. Datové soubory mohou obsahovat soubory libovolného typu: textové soubory, soubory XML nebo dokonce soubory databáze aplikace Microsoft Access ( *MDB* ). Následující postupy ukazují, jak přidat datový soubor libovolného typu do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.

### <a name="to-include-a-data-file-by-using-mageexe"></a>Zahrnutí datového souboru pomocí Mage.exe

1. Přidejte datový soubor do adresáře aplikace se zbytkem souborů vaší aplikace.

    Adresář aplikace bude obvykle adresář označený aktuální verzí nasazení, například v 1.0.0.0.

2. Aktualizujte svůj manifest aplikace a seznamte se s datovým souborem.

    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`

    Provedením této úlohy znovu vytvoříte seznam souborů v manifestu aplikace a také automaticky vygenerujete signatury hash.

3. Otevřete manifest aplikace v preferovaném textovém editoru nebo editoru XML a vyhledejte `file` element pro nedávno přidaný soubor.

    Pokud jste přidali soubor XML s názvem `Data.xml` , soubor bude vypadat podobně jako v následujícím příkladu kódu.

   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

4. Přidejte atribut `type` k tomuto prvku a zadejte jej s hodnotou `data` .

   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`

5. Svůj manifest aplikace znovu podepište pomocí páru klíčů nebo certifikátu a pak znovu podepište manifest nasazení.

    Manifest nasazení je nutné znovu podepsat, protože jeho hodnota hash manifestu aplikace se změnila.

    `mage -s app manifest -cf cert_file -pwd password`

    `mage -u deployment manifest -appm app manifest`

    `mage -s deployment manifest -cf certfile -pwd password`

### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Zahrnutí datového souboru pomocí MageUI.exe

1. Přidejte datový soubor do adresáře aplikace se zbytkem souborů vaší aplikace.

2. Adresář aplikace bude obvykle adresář označený aktuální verzí nasazení, například v 1.0.0.0.

3. V nabídce **soubor** klikněte na **otevřít** a otevřete svůj manifest aplikace.

4. Vyberte kartu **soubory** .

5. Do textového pole v horní části karty zadejte adresář, který obsahuje soubory vaší aplikace, a potom klikněte na **vyplnit**.

     Datový soubor se zobrazí v mřížce.

6. Nastavte hodnotu **typ souboru** datového souboru na **data**.

7. Uložte manifest aplikace a pak znovu podepište soubor.

     *MageUI.exe* vás vyzve k opětovnému podepsání souboru.

8. Opětovné podepsání manifestu nasazení

     Manifest nasazení je nutné znovu podepsat, protože jeho hodnota hash manifestu aplikace se změnila.

## <a name="see-also"></a>Viz také
- [Přístup k místním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)