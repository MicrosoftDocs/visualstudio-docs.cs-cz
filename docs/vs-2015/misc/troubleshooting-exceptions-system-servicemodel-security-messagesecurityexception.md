---
title: 'Řešení potíží s výjimkami: System. ServiceModel. Security. MessageSecurityException – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b8ce3f16c1439d62cfa1e2cff344b70e6724c42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655356"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Řešení potíží s výjimkami: System.ServiceModel.Security.MessageSecurityException
Výjimka <xref:System.ServiceModel.Security.MessageSecurityException> je vyvolána, když [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] určuje, že zpráva není správně zabezpečena nebo byla poškozena. K chybě dochází nejčastěji v případě, že jsou splněny následující podmínky:

- Odkaz na službu WCF se používá přes vzdálené připojení, například Připojení ke vzdálené ploše nebo Terminálové služby ke komunikaci se službou WCF (. svc) na webu nebo v projektu webové aplikace.

- Ve vzdálené lokalitě nemáte oprávnění správce.

- Požadavky na localhost na vzdálené lokalitě jsou zpracovávány [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]m vývojovým serverem.

## <a name="associated-tips"></a>Přidružené tipy
 **Řešení problémů s ověřováním NTLM při použití vývojového serveru ASP.Net**
@No__t_0 vývojový server má obvykle vypnuté zabezpečení Windows NT Challenge/Response (NTLM), které umožňuje anonymní přístup. Ve výchozím nastavení platí, že když spouštíte relaci Terminálové služby nebo používáte vzdálené připojení, je zapnuté zabezpečení NTLM. Je-li povolen protokol NTLM, jsou všechny požadavky localhost ověřovány proti přihlašovacím údajům uživatele nebo procesu, který spustil [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový server. Tím se sníží bezpečnostní hrozby. WCF ale také provádí vlastní ověřování a neumožňuje účtu bez oprávnění správce využívat služby WCF.

 Pokud vzdálený uživatel může web spustit pomocí [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] vývojový server a také pracovat s webovou službou nebo službou WCF, můžete buď vytvořit vlastní vazbu služby, nebo vypnout zabezpečení NTLM.

> [!IMPORTANT]
> Vypnutí zabezpečení NTLM není doporučeno a může představovat bezpečnostní riziko.

 Pokud vytvoříte vlastní vazbu služby, budete i nadále chráněni ověřováním NTLM.

 Pomocí následujících kroků můžete vytvořit vlastní vazbu služby pro službu WCF.

#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Vytvoření vlastní vazby služby pro službu WCF hostovanou ve vývojovém serveru ASP.NET

1. Otevřete soubor Web. config pro službu WCF, která generuje výjimku.

2. Do souboru Web. config zadejte následující informace.

   ```
   <bindings>
     <customBinding>
       <binding name="Service1Binding">
         <transactionFlow />
         <textMessageEncoding />
         <httpTransport authenticationScheme="Ntlm" />
       </binding>
     </customBinding>
   </bindings>
   ```

3. Uložte a zavřete soubor Web. config.

4. V kódu pro WCF nebo webovou službu změňte hodnotu koncového bodu na následující:

   ```
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />
   ```

    Tím se zajistí, že služba používá vlastní vazbu.

5. Přidejte odkaz na službu ve webové aplikaci, která přistupuje ke službě. (V dialogovém okně **Přidat odkaz na službu** přidejte odkaz na službu jako u původní služby, která generovala výjimku.)

   Pomocí těchto kroků můžete zakázat zabezpečení protokolu NTLM při práci s odkazem na službu WCF.

> [!IMPORTANT]
> Vypnutí zabezpečení NTLM není doporučeno a může představovat bezpečnostní riziko.

#### <a name="to-turn-off-ntlm-security"></a>Vypnutí zabezpečení NTLM

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název webu a potom klikněte na položku **stránky vlastností**.

2. Vyberte **Možnosti spuštění**a potom zrušte zaškrtnutí políčka **ověřování NTLM** .

3. Klikněte na tlačítko **OK**.

## <a name="see-also"></a>Viz také
 <xref:System.ServiceModel.Security.MessageSecurityException> [použít Pomocníka pro výjimky](https://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)