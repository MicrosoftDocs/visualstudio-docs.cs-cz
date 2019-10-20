---
title: Mezipaměť schématu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 35a7fcad-f3bf-4a96-9008-4306e7276223
caps.latest.revision: 10
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: feae3dbc18f0b009b88872c05d43e9a6c280aef5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656171"
---
# <a name="schema-cache"></a>Mezipaměť schémat
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Editor XML poskytuje mezipaměť schématu umístěnou v adresáři%InstallRoot%\Xml\Schemas. Mezipaměť schématu je globální pro všechny uživatele ve vašem počítači a obsahuje standardní schémata XML, která se používají pro technologii IntelliSense a ověřování dokumentů XML.

 Editor XML může také vyhledat schémata nacházející se v řešení, schémata uvedená v poli **schémata** v okně **vlastnosti** dokumentu a schémata identifikovaná `xsi:schemaLocation` a `xsi:noNamespaceSchemaLocation` atributy.

 Následující tabulka popisuje schémata, která jsou nainstalována s editorem XML.

|     Bitmap      |                                                      Popis                                                      |
|-------------------|-----------------------------------------------------------------------------------------------------------------------|
|    Catalog. xsd    |             Schéma pro soubory katalogu schématu editoru XML Informace o katalozích schématu najdete níže.             |
| Soubor DotNetConfig. xsd  |                 Schéma pro soubory Web. config, "<http://schemas.microsoft.com/.NETConfiguration/v2.0>".                 |
|    MSBuild. xsd    |              Schéma pro MSBuild vytvořit soubory "<http://schemas.microsoft.com/developer/msbuild/2003>".              |
|    msdata. xsd     | Schéma pro poznámky XSD přidané třídou <xref:System.Data.DataSet>, "urn: schemas-microsoft-com: XML-msdata". |
|     msxsl. xsd     |                  Schéma pro rozšíření bloků skriptu Microsoft XSLT, urn: schemas-microsoft-com: XSLT.                   |
| SnippetFormat. xsd |                 Schéma pro soubory XML fragmentu kódu. Příklady najdete v tématu% InstallDir% \VC#\Expansions.                 |
|    SOAP 1.1. xsd    |            Schéma pro protokol SOAP (Simple Object Access Protocol) 1,1, http://schemas.xmlsoap.org/soap/envelope/.            |
|    SOAP 1.2. xsd    |                                     Schéma pro Simple Object Access Protocol 1,2.                                     |
| SiteMapSchema. xsd |            Schéma pro soubor XML mapy webu ASP.NET "<http://schemas.microsoft.com/AspNet/SiteMap-File-1.0>".             |
|     WSDL. xsd      |                    Schéma pro jazyk popisu webové služby http://schemas.xmlsoap.org/wsdl/.                     |
|     xenc. xsd      |                            Schéma pro šifrování XML http://www.w3.org/2000/09/xmldsig#.                             |
|     XHTML. xsd     |                                    Schéma pro XHTML http://www.w3.org/1999/xhtml.                                     |
|     XLink. xsd     |                                  Schéma pro XLink 1.0 http://www.w3.org/1999/xlink.                                   |
|      XML. xsd      |              Schéma popisující XML: Space a XML: lang atributy, http://www.w3.org/XML/1998/namespace.               |
|    xmlsig. xsd     |                        Schéma pro digitální podpisy XML http://www.w3.org/2000/09/xmldsig#.                         |
|   xsdschema. xsd   |                            Schéma popisující samotný XSD, http://www.w3.org/2001/XMLSchema.                            |
|     XSLT. xsd      |                           Schéma pro transformace XML http://www.w3.org/1999/XSL/Transform.                            |

## <a name="updating-schemas-in-the-cache"></a>Aktualizace schémat v mezipaměti
 Editor načte adresář mezipaměti schématu, když je načten balíček editoru XML a sleduje všechny změny při spuštění. Pokud bylo schéma přidáno, je automaticky načteno do indexu v paměti známých schémat. Pokud se schéma odebralo, automaticky se odebere z indexu v paměti. Pokud se schéma aktualizovalo, automaticky neověřuje mezipaměť v paměti tohoto schématu.

> [!NOTE]
> Vzhledem k tomu, že adresář mezipaměti schémat je globální pro váš počítač, měli byste přidat pouze schémata, která jsou Standard a užitečná pro všechny projekty sady Visual Studio, které mohou být vytvořeny v počítači.

 Editor XML také podporuje libovolný počet souborů katalogu schémat v adresáři mezipaměti schématu. Katalogy schémat mohou ukazovat na jiná umístění pro schémata, o kterých má Editor vždy informace. Soubor Catalog. xsd definuje formát souboru katalogu a je zahrnutý v adresáři mezipaměti schématu. Soubor Catalog. XML je výchozím katalogem a obsahuje odkazy na jiná schémata v% InstallDir%. Následuje vzorkování souboru Catalog. XML:

```
<SchemaCatalog xmlns="http://schemas.microsoft.com/xsd/catalog">
  <Schema href="%InstallDir%/help/schemas/Favorites.xsd" targetNamespace="urn:Favorites-Schema"/>
  <Schema href="%InstallDir%/help/schemas/Links.xsd" targetNamespace="urn:Links-Schema"/>
  <Schema href="%InstallDir%/help/schemas/MyHelp.xsd" targetNamespace="urn:VSHelp-Schema"/>
</SchemaCatalog>
```

 Atribut `href` může být libovolná cesta k souboru nebo adresa URL protokolu HTTP odkazující na schéma. Cesta k souboru může být relativní vzhledem k dokumentu katalogu. Následující proměnné, oddělené%%, jsou rozpoznávány editorem a budou rozšířeny v cestě:

- InstallDir

- Systém

- ProgramFiles

- Programy

- CommonProgramFiles

- ApplicationData

- CommonApplicationData

- IDENTIFIKÁTORY

  Katalogový dokument může zahrnovat `Catalog` element, který odkazuje na jiné katalogy. Pomocí elementu `Catalog` můžete odkazovat na centrální katalog sdílený vaším týmem nebo společností nebo online katalog sdílený s vašimi obchodními partnery. Atribut `href` je cesta k souboru nebo adresa URL protokolu HTTP pro ostatní katalogy. Následuje příklad prvku `Catalog`:

```
<Catalog href="file://c:/xcbl/xcblCatalog.xml"/>
```

 Katalog také může řídit, jak jsou schémata přidružena k dokumentům XML pomocí speciálního prvku `Association`. Tento prvek přidruží schémata, které nemají žádný cílový obor názvů s konkrétní příponou souboru, což může být užitečné, protože editor XML neprovede žádné automatické přidružení schémat, které nemají atribut `targetNamespace`. V následujícím příkladu `Association` prvek přidruží schéma soubor DotNetConfig ke všem souborům, které mají příponu souboru "config":

```
<Association extension="config" schema="%InstallDir%/xml/schemas/dotNetConfig.xsd"/>
```

## <a name="localized-schemas"></a>Lokalizovaná schémata
 V mnoha případech soubor Catalog. XML neobsahuje položky pro lokalizovaná schémata. Do souboru Catalog. XML můžete přidat další položky, které odkazují na lokalizovaný adresář schématu.

 V následujícím příkladu byl vytvořen nový prvek `Schema`, který používá proměnnou% LCID%, aby odkazovala na lokalizované schéma.

```
<Schema href="%InstallRoot%/Common7/IDE/Policy/Schemas/%LCID%/TDLSchema.xsd"
  targetNamespace="http://www.microsoft.com/schema/EnterpriseTemplates/TDLSchema"/>
```

## <a name="changing-the-location-of-the-schema-cache"></a>Změna umístění mezipaměti schématu
 Umístění mezipaměti schématu můžete přizpůsobit pomocí stránky **různé** možnosti. Pokud máte adresář oblíbených schémat, lze Editor nakonfigurovat tak, aby místo toho používal schémata.

> [!NOTE]
> Tato změna bude mít vliv pouze na aktuálního uživatele sady Visual Studio.

#### <a name="to-change-the-schema-cache-location"></a>Změna umístění mezipaměti schématu

1. V nabídce **nástroje** vyberte možnost **Možnosti**.

2. Rozbalte položku **textový editor**, rozbalte položku **XML**a potom klikněte na možnost **různé**.

3. Klikněte na tlačítko **Procházet** v poli **schémata** .

4. Vyberte složku pro mezipaměť schématu a klikněte na tlačítko **OK**.

#### <a name="to-add-another-directory-of-common-schemas"></a>Přidání dalšího adresáře běžných schémat

1. Upravte soubor Catalog. XML v adresáři mezipaměti schématu editoru XML.

2. Přidejte nový prvek `<Catalog href="…"/>`, který odkazuje na adresář dalších schémat.

3. Uložte provedené změny.

     Katalog se automaticky znovu načte.

## <a name="see-also"></a>Viz také
 [Editor XML](../xml-tools/xml-editor.md)
