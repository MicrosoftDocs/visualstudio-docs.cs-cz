---
title: 'Postupy: definování deskriptoru typu pro parametr | Microsoft Docs'
description: Naučte se definovat popisovač typu parametru pro metodu v modelu služby připojení obchodních dat (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8044f04902e74b2597d6cf331e54eb4a6138817a
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94903595"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Postupy: definování deskriptoru typu pro parametr
  Popisovač typu obsahuje vlastnosti, které popisují datový typ parametru. Deskriptor typu může definovat pole, entitu nebo kolekci entit. Další informace naleznete v tématu [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-the-type-descriptor-of-a-parameter"></a>Definování deskriptoru typu pro parametr

1. V okně **Podrobnosti metody služby BDC** vyberte popisovač typu parametru.

2. Na panelu nabídek vyberte možnost **zobrazení**, **okno Vlastnosti**.

3. V okně **vlastnosti** nastavte vlastnosti popisovače typu.

     Následující postupy popisují, jak definovat popisovač typu jako pole, entitu nebo kolekci entit.

### <a name="to-define-a-field"></a>Definování pole

1. V okně **vlastnosti** nastavte vlastnost **název** popisovače typu na název pole v typu, který představuje entitu (například: **FirstName**).

2. V seznamu vedle vlastnosti **TypeName** vyberte vhodný datový typ (například **Int32**).

     Informace o dalších volitelných parametrech naleznete v tématu [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).

### <a name="to-define-an-entity"></a>Definování entity

1. V okně **vlastnosti** nastavte vlastnost **název** na název, který popisuje entitu (například: **kontakt**).

2. Nastavte vlastnost **TypeName** na plně kvalifikovaný název typu, který představuje entitu. Tento typ může být třída ve vašem projektu, typ definovaný v sestavení, na které odkazujete ve svém řešení, nebo typ definovaný v objektovém modelu služby BDC.

    - Pro třídu ve vašem projektu zvolte šipku dolů vedle vlastnosti **TypeName** , zvolte kartu **aktuální projekt** v dialogovém okně, které se zobrazí, a pak zvolte třídu v projektu.

         Plně kvalifikovaný název obsahuje obor názvů a název třídy následovaný názvem systému LOB. Následující příklad nastaví hodnotu vlastnosti **TypeName** na třídu ve vašem projektu.

         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`

    - Pro typ umístěný v sestavení v rámci vašeho řešení obsahuje plně kvalifikovaný název název typu, název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.

         Následující příklad nastaví hodnotu vlastnosti **TypeName** na typ definovaný v sestavení, na které odkazujete ve svém řešení.

         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`

    - Pro typ definovaný v objektovém modelu služby BDC obsahuje plně kvalifikovaný název obor názvů a název typu.

         Následující příklad nastaví hodnotu vlastnosti **TypeName** na typ v objektovém modelu služby BDC.

         `Microsoft.BusinessData.Runtime.DynamicType`

3. V okně **Podrobnosti metody služby BDC** otevřete seznam, který se zobrazí pro popisovač typu, a pak zvolte **Upravit**.

     Otevře se okno **Průzkumník služby BDC** .

4. V **Průzkumníku služby BDC** otevřete místní nabídku popisovače typu a pak zvolte **Přidat popisovač typu**.

     Nový popisovač typu je přidán jako podřízený k popisovači typu entity. Nakonfigurujte tento popisovač typu jako pole.

5. Opakujte krok 4 pro přidání popisovače podřízeného typu pro každé pole entity.

### <a name="to-define-a-collection-of-entities"></a>Definování kolekce entit

1. V okně **Podrobnosti metody služby BDC** vyberte popisovač typu parametru, který chcete.

2. Na panelu nabídek vyberte možnost **zobrazení**, **okno Vlastnosti**.

3. V okně **vlastnosti** nastavte vlastnost **název** na název, který popisuje entitu (například: **Contacts**).

4. Nastavte vlastnost **IsCollection** na **hodnotu true**. To znamená, že tento popisovač typu je kolekcí entit.

5. Nastavte vlastnost **TypeName** na řetězec, který obsahuje odkaz na <xref:System.Collections.Generic.IEnumerable%601> rozhraní a plně kvalifikovaný název typu, který představuje entitu. Tento typ může být třída ve vašem projektu, typ definovaný v sestavení, na které odkazujete ve svém řešení, nebo typ definovaný v objektovém modelu služby BDC.

   - Pro třídu ve vašem projektu zvolte šipku dolů vedle vlastnosti **TypeName** , zvolte kartu **aktuální projekt** v dialogovém okně, které se zobrazí, a pak zvolte třídu v projektu.

      Plně kvalifikovaný název obsahuje obor názvů a název třídy následovaný názvem systému LOB.

      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci tříd v projektu.

      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace. BdcModel1. Contact, BdcModel1]

   - Pro typ umístěný v sestavení v rámci vašeho řešení obsahuje plně kvalifikovaný název název typu, název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.

      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci typů v sestavení, na které odkazujete ve svém řešení.

      `System.Collections.Generic.IEnumerable`1 [MyNamespace. Contact, myAssemblyName, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089]

   - Pro typ definovaný v objektovém modelu služby BDC obsahuje plně kvalifikovaný název pouze obor názvů a název typu.

      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci typů definovaných v objektovém modelu služby BDC.

      `System.Collections.Generic.IEnumerable`1 [Microsoft. BusinessData. Runtime. DynamicType] '

6. V okně **Podrobnosti metody služby BDC** otevřete seznam, který se zobrazí pro popisovač typu, a pak zvolte **Upravit**.

    Otevře se okno **Průzkumník služby BDC** .

7. V **Průzkumníku služby BDC** otevřete místní nabídku popisovače typu a pak zvolte **Přidat popisovač typu**.

    Nový popisovač typu je přidán jako podřízený popisovač typu kolekce. Tento deskriptor typu nakonfigurujte jako entitu.

## <a name="see-also"></a>Viz také
- [Přehled nástrojů pro návrh modelu služby BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Postupy: Přidání parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)
- [Návrh modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)
