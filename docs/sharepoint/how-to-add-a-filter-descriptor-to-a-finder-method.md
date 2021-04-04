---
title: 'Postupy: Přidání deskriptoru filtru do vyhledávací metody | Microsoft Docs'
description: Zjistěte, jak přidat popisovač filtru k metodě hledání pomocí okna podrobnosti metody služby BDC v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], filter descriptors
- Business Data Connectivity service [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], add a filter
- BDC [SharePoint development in Visual Studio], filter descriptors
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 47fcc7e388f240d8b9636a733df4b6b8767f0df4
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218006"
---
# <a name="how-to-add-a-filter-descriptor-to-a-finder-method"></a>Postupy: Přidání deskriptoru filtru do vyhledávací metody
  Deskriptory filtru umožňují spotřebitelům modelu předat hodnoty metodám před jejich spuštěním. Další informace najdete v tématu [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md).

 Jedním z běžných scénářů je, že uživatelé v SharePointu chtějí načíst instance externího typu obsahu, které odpovídají určitým kritériím. Tento scénář můžete podporovat přidáním popisovače filtru k metodě hledání.

### <a name="to-add-a-filter-descriptor-to-a-finder-method"></a>Přidání deskriptoru filtru do vyhledávací metody

1. V okně **Podrobnosti metody služby BDC** rozbalte uzel vyhledávací metody, rozbalte uzel **parametry** a přidejte vstupní parametr. Další informace naleznete v tématu [How to: Add a parametr to a Method](../sharepoint/how-to-add-a-parameter-to-a-method.md).

2. V okně **Podrobnosti metody** vyberte popisovač typu parametru.

3. Na panelu nabídek vyberte možnost **Zobrazit**  >  **okno vlastností**.

4. V okně **vlastnosti** nastavte vlastnost **název typu** na datový typ, který je vhodný pro filtr.

     Filtr může například použít datum objednávky k omezení počtu prodejních objednávek vrácených metodou. Pro podporu tohoto filtru musí být vlastnost **název typu** deskriptoru typu nastavená na **System. DateTime**.

5. V okně **Podrobnosti o metodě** rozbalte uzel **popisovače filtru** .

6. V seznamu **Přidat Deskriptor filtru** vyberte možnost **vytvořit popisovač filtru**.

     Pod uzlem **popisovače filtru** se zobrazí nový popisovač filtru.

7. Na panelu nabídek vyberte možnost **Zobrazit**  >  **okno vlastností**.

8. V okně **vlastnosti** vyberte vlastnost **typ** .

9. V seznamu, který se zobrazí pro vlastnost **typ** , vyberte požadovaný vzor filtrování.

     Chcete-li například vytvořit filtr, který používá datum objednávky k omezení počtu prodejních objednávek vrácených v metodě hledání, vyberte možnost **porovnání**. Filtr porovnání zajišťuje, že metoda vyhledávání vrátí pouze ty instance, které splňují určitou podmínku. Další informace o jednotlivých vzorech filtrování najdete v tématu [typy filtrů podporované službou BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

10. V okně **vlastnosti** vyberte vlastnost **popisovače přidruženého typu** .

11. V seznamu, který se zobrazí pro vlastnost **přidružených popisovačů typu** , vyberte popisovač typu, který jste vytvořili dříve v tomto postupu. Tím se filtr vztahuje na vstupní parametr vyhledávací metody.

12. Přidejte kód do metody Finder, která vrací data. Vstupní parametr můžete použít jako podmínku v dotazu Select.

     Následující příklad vrátí prodejní objednávky, které mají zadané datum objednávky.

    > [!NOTE]
    > Hodnotu pole nahraďte `ServerName` názvem vašeho serveru.

     :::code language="csharp" source="../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs" id="Snippet11":::
     :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb" id="Snippet11":::

## <a name="see-also"></a>Viz také
- [Postupy: Přidání vyhledávací metody](../sharepoint/how-to-add-a-finder-method.md)
- [Postupy: Přidání konkrétní vyhledávací metody](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování deskriptoru typu pro parametr](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Integrace obchodních dat do služby SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
