---
title: 'Postupy: zahrnutí datového souboru do aplikace ClickOnce | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cfba7612ec0e019b8c8dfa7c7406435b6e43e6cc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917918"
---
# <a name="how-to-include-a-data-file-in-a-clickonce-application"></a>Postupy: zahrnutí datového souboru do aplikace ClickOnce
Každý [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikaci nainstalujete, je přiřazen adresář data na místním disku cílového počítače, kde aplikace může spravovat svoje vlastní data. Datové soubory můžete zahrnout soubory libovolného typu: textové soubory, soubory XML nebo dokonce i databáze Microsoft Access (*.mdb*) soubory. Následující postupy ukazují, jak přidat soubor dat libovolného typu do vašeho [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikace.  
  
### <a name="to-include-a-data-file-by-using-mageexe"></a>Zahrnout soubor dat s využitím Mage.exe  
  
1. Přidáte datový soubor do adresáře aplikace se zbytkem soubory vaší aplikace.  
  
    Obvykle adresáře aplikace bude označen s aktuální verzí nasazení – například v1.0.0.0.  
  
2. Aktualizujte manifest aplikace do seznamu datový soubor.  
  
    `mage -u v1.0.0.0\Application.manifest -FromDirectory v1.0.0.0`  
  
    Jak tento úkol provést znovu vytvoří seznam souborů v manifestu aplikace a také automaticky vygeneruje podpisy hodnoty hash.  
  
3. Otevřete manifest aplikace v upřednostňovaném textovém editoru nebo editoru XML a najděte `file` – element pro nedávno přidaný soubor.  
  
    Pokud jste přidali soubor XML s názvem `Data.xml`, soubor bude vypadat podobně jako v následujícím příkladu kódu.  
  
   `<file name="Data.xml" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
4. Přidejte atribut `type` na tento element a zadejte ji s hodnotou `data`.  
  
   `<file name="Data.xml" writeableType="applicationData" hash="23454C18A2DC1D23E5B391FEE299B1F235067C59" hashalg="SHA1" asmv2:size="39500" />`  
  
5. Znovu podepsat manifest aplikace pomocí páru klíčů nebo certifikát a nové podepsání manifestu nasazení.  
  
    Musíte znovu podepsat manifestu nasazení, protože došlo ke změně jeho hodnoty hash manifestu aplikace.  
  
    `mage -s app manifest -cf cert_file -pwd password`
  
    `mage -u deployment manifest -appm app manifest`
  
    `mage -s deployment manifest -cf certfile -pwd password`
  
### <a name="to-include-a-data-file-by-using-mageuiexe"></a>Zahrnout soubor dat s využitím MageUI.exe  
  
1.  Přidáte datový soubor do adresáře aplikace se zbytkem soubory vaší aplikace.  
  
2.  Obvykle adresáře aplikace bude označen s aktuální verzí nasazení – například v1.0.0.0.  
  
3.  Na **souboru** nabídky, klikněte na tlačítko **otevřete** otevřete manifest aplikace.  
  
4.  Vyberte **soubory** kartu.  
  
5.  Do textového pole v horní části karty zadejte adresář, který obsahuje soubory vaší aplikace a pak klikněte na tlačítko **naplnit**.  
  
     Datový soubor se zobrazí v mřížce.  
  
6.  Nastavte **typ souboru** hodnotu datového souboru **Data**.  
  
7.  Uložit manifest aplikace a opětovné podepsání souboru.  
  
     *MageUI.exe* vás vyzve k opětovné podepsání souboru.  
  
8.  Opětovné podepsání manifestu nasazení  
  
     Musíte znovu podepsat manifestu nasazení, protože došlo ke změně jeho hodnoty hash manifestu aplikace.  
  
## <a name="see-also"></a>Viz také:  
 [Přístup k lokálním a vzdáleným datům v aplikacích ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)