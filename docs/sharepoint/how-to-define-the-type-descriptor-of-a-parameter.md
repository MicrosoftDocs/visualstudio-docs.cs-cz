---
title: 'Postupy: definování deskriptoru typu pro parametr | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor
- BDC [SharePoint development in Visual Studio], parameter types
- BDC [SharePoint development in Visual Studio], type descriptor
- Business Data Connectivity service [SharePoint development in Visual Studio], parameter types
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ec2b0173838446c770f3323aacefebabc195c48b
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294978"
---
# <a name="how-to-define-the-type-descriptor-of-a-parameter"></a>Postupy: definování deskriptoru typu pro parametr
  Popisovač typu obsahuje vlastnosti, které popisují datový typ parametru. Popisovač typu může definovat pole, entitu nebo kolekci entit. Další informace najdete v tématu [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-the-type-descriptor-of-a-parameter"></a>K definování deskriptoru typu pro parametr  
  
1.  V **podrobnosti metody služby BDC** okna, vyberte typ popisovače parametru.  
  
2.  V panelu nabídky zvolte **zobrazení**, **okno vlastností**.  
  
3.  V **vlastnosti** okno, nastavte vlastnosti popisovače typu.  
  
     Následující postupy popisují, jak definovat popisovač typu jako pole, entitu nebo kolekci entit.  
  
### <a name="to-define-a-field"></a>Definování pole  
  
1.  V **vlastnosti** okno, nastaveno **název** vlastnosti popisovače typu na název pole v typu, který představuje entitu (například: **FirstName**).  
  
2.  V seznamu vedle **TypeName** vlastnosti, vyberte odpovídající typ dat (například **Int32**).  
  
     Informace o dalších volitelných parametrech naleznete v tématu [TypeDescriptor](/previous-versions/office/developer/sharepoint-2007/ms543392\(v\=office.12\)).  
  
### <a name="to-define-an-entity"></a>Definování entity  
  
1.  V **vlastnosti** okno, nastaveno **název** nastavte na název, který popisuje entitu (například: **kontakt**).  
  
2.  Nastavte **TypeName** vlastnost na plně kvalifikovaný název typu, který entitu představuje. Tento typ může být třída v projektu, typ definovaný v sestavení, na které odkazujete ve svém řešení nebo typ definovaný v objektovém modelu služby BDC.  
  
    -   Pro třídu ve vašem projektu, zvolte šipku dolů vedle možnosti **TypeName** vlastnost, zvolte **aktuální projekt** kartu v dialogovém okně, které se zobrazí a pak zvolte třídu v projektu.  
  
         Plně kvalifikovaný název obsahuje obor názvů a název třídy následovaný názvem systému LOB. Následující příklad nastaví hodnotu vlastnosti **TypeName** na třídu ve vašem projektu.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Pro typ umístěný v sestavení ve vašem řešení plně kvalifikovaný název obsahuje název typu, název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.  
  
         Následující příklad nastaví hodnotu vlastnosti **TypeName** na typ definovaný v sestavení, na které odkazujete ve svém řešení.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Pro typ definovaný v objektovém modelu služby BDC plně kvalifikovaný název obsahuje obor názvů a název typu.  
  
         Následující příklad nastaví hodnotu vlastnosti **TypeName** na typ v objektovém modelu služby BDC.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  V **podrobnosti metody služby BDC** okno, otevřete seznam, který se zobrazí pro typ popisovače a klikněte na tlačítko **upravit**.  
  
     **Služby BDC Explorer** otevře se okno.  
  
4.  V **služby BDC Explorer**, otevřete místní nabídku popisovače typu a klikněte na tlačítko **přidat popisovač typu**.  
  
     Nový typ popisovače je přidán jako podřízený do popisovače typu entity. Nakonfigurujte tento typ popisovače jako pole.  
  
5.  Opakujte krok 4 pro přidání podřízeného popisovače typu pro každé pole entity.  
  
### <a name="to-define-a-collection-of-entities"></a>Definovaní kolekce entit  
  
1. V **podrobnosti metody služby BDC** okna, vyberte typ popisovače parametru, který chcete.  
  
2. V panelu nabídky zvolte **zobrazení**, **okno vlastností**.  
  
3. V **vlastnosti** okno, nastaveno **název** nastavte na název, který popisuje entitu (například: **kontakty**).  
  
4. Nastavte **IsCollection** vlastnost **True**. To znamená, že tento typ popisovače je kolekce entit.  
  
5. Nastavte **TypeName** nastavte na řetězec, který obsahuje odkaz na <xref:System.Collections.Generic.IEnumerable%601> rozhraní a plně kvalifikovaný název typu, který entitu představuje. Tento typ může být třída v projektu, typ definovaný v sestavení, na které odkazujete ve svém řešení nebo typ definovaný v objektovém modelu služby BDC.  
  
   - Pro třídu ve vašem projektu, zvolte šipku dolů vedle možnosti **TypeName** vlastnost, zvolte **aktuální projekt** kartu v dialogovém okně, které se zobrazí a pak zvolte třídu v projektu.  
  
      Plně kvalifikovaný název obsahuje obor názvů a název třídy následovaný názvem systému LOB.  
  
      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci tříd ve vašem projektu.  
  
      `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` ` BdcModel1.Contact, BdcModel1] "  
  
   - Pro typ umístěný v sestavení ve vašem řešení plně kvalifikovaný název obsahuje název typu, název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.  
  
      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci typů v sestavení, na které odkazujete ve svém řešení.  
  
      `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, verze = 4.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089] "  
  
   - Pro typ definovaný v objektovém modelu služby BDC plně kvalifikovaný název obsahuje pouze obor názvů a název typu.  
  
      Následující příklad nastaví hodnotu vlastnosti **TypeName** na kolekci typů definovaných v objektovém modelu služby BDC.  
  
      `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType] "  
  
6. V **podrobnosti metody služby BDC** okno, otevřete seznam, který se zobrazí pro typ popisovače a klikněte na tlačítko **upravit**.  
  
    **Služby BDC Explorer** otevře se okno.  
  
7. V **služby BDC Explorer**, otevřete místní nabídku popisovače typu a klikněte na tlačítko **přidat popisovač typu**.  
  
    Nový typ popisovače je přidán jako podřízený do popisovače typu kolekce. Nakonfigurujte tento typ popisovače jako entitu.  
  
## <a name="see-also"></a>Viz také:
 [Přehled nástroje pro navrhování modelů služby BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Postupy: Přidání entity do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Postupy: Přidání parametru k metodě](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Postupy: definování instance metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Navrhování modelu připojení obchodních dat](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
