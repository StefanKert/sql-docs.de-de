---
title: Erstellen einer Dimension anhand einer vorhandenen Tabelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], dimensions
- main dimension tables
- dimensions [Analysis Services], standard
- standard dimensions [Analysis Services]
ms.assetid: edd96fbe-1b1c-445a-95d6-7a025e0ee868
caps.latest.revision: 52
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 9ff912d4c828efec8bacd163ae6b47f980a94beb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2018
ms.locfileid: "37319250"
---
# <a name="create-a-dimension-by-using-an-existing-table"></a>Erstellen einer Dimension anhand einer vorhandenen Tabelle
  In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]können Sie mit dem Dimensions-Assistenten von [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] eine Dimension aus einer vorhandenen Tabelle erstellen. Hierzu wählen Sie auf der Seite **Erstellungsmethode auswählen** des Assistenten die Option **Vorhandene Tabelle verwenden** aus. Wenn Sie diese Option auswählen, basiert der Assistent die Dimensionsstruktur auf den Dimensionstabellen, ihren Spalten und allen Beziehungen zwischen diesen Spalten in einer vorhandenen Datenquellensicht. Der Assistent prüft die Daten in der Quelltabelle und den verknüpften Tabellen. Er verwendet diese Daten, um Attributspalten zu definieren, die auf den Spalten in den Dimensionstabellen basieren, und um Attributhierarchien (auch *benutzerdefinierte* Hierarchien genannt) zu definieren. Nachdem Sie mit dem Dimensions-Assistenten Ihre eigene Dimension erstellt haben, können Sie den Dimensions-Designer zum Hinzufügen, Entfernen und Konfigurieren von Attributen und Hierarchien in der Dimension verwenden.  
  
 Wenn Sie eine Dimension anhand einer vorhandenen Tabelle erstellen, führt Sie der Dimensions-Assistent durch die folgenden Schritte:  
  
-   Angeben der Quellinformationen  
  
-   Auswählen von verknüpften Tabellen  
  
-   Auswählen von Dimensionsattributen  
  
-   Definieren der Kontointelligenz  
  
> [!NOTE]  
>  Ausführliche Anweisungen zu den in diesem Thema enthaltenen Informationen finden Sie unter [Erstellen einer Dimension mit dem Dimensions-Assistenten](create-a-dimension-using-the-dimension-wizard.md).  
  
## <a name="specifying-the-source-information"></a>Angeben der Quellinformationen  
 Zum Angeben der Quellinformationen verwenden Sie die Seite **Quellinformationen angeben** . Zunächst wählen Sie die Datenquellensicht aus, die die Tabelle enthält, auf der die Dimension basieren soll. Anschließend geben Sie die Hauptdimensionstabelle für die zu definierende Dimension an. Die Hauptdimensionstabelle ist die Tabelle, die direkt mit der Faktentabelle verknüpft ist. Beispielsweise können Sie eine <localizedText>Product</localizedText>-Tabelle als Haupttabelle für eine <localizedText>Products</localizedText>-Dimension oder eine <localizedText>Employee</localizedText>-Tabelle für eine <localizedText>Employees</localizedText>-Dimension angeben. Der Assistent wählt automatisch eine Schlüsselspalte aus, die auf dem Primärschlüssel in der Datenquellensicht basiert. Sie können die Schlüsselspalte jedoch wie gewünscht ändern. Über die Schlüsselspalte werden die Elemente der Dimension bestimmt. Für eine <localizedText>Product</localizedText>-Dimension würden Sie z. B. <localizedText>ProductKey</localizedText> als Schlüsselspalte definieren.  
  
 Optional können Sie eine Spalte definieren, die den Elementnamen enthält. Der Elementname, der den Benutzern angezeigt wird, ist standardmäßig der Wert aus der Schlüsselspalte. Die Werte in einer Schlüsselspalte, z. B. <localizedText>ProductID</localizedText> oder <localizedText>EmployeeID</localizedText>, sind häufig eindeutige, vom System generierte Schlüssel, die für die Benutzer nicht aussagekräftig sind. Häufig können Sie den Benutzern aussagekräftigere Informationen bereitstellen, indem Sie den Namen, den die Benutzer sehen, in einen entsprechenden Wert in einer anderen Spalte der Dimension ändern. Beispielsweise können Sie eine Elementnamensspalte definieren, die Produkt- oder Mitarbeiternamen enthält. Wenn Sie den Elementnamen ändern, wird den Benutzern ein aussagekräftiger Name angezeigt. In Abfragen werden jedoch weiterhin die Werte aus der Schlüsselspalte verwendet, um zwischen Elementen mit gleichem Namen unterscheiden zu können. Wenn Sie für die Schlüsselspalte einen zusammengesetzten Schlüssel angeben, müssen Sie auch die Spalte angeben, die die Elementwerte für das Schlüsselattribut bereitstellt. Weitere Informationen zum Konfigurieren von Attributeigenschaften finden Sie unter [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md).  
  
## <a name="selecting-related-tables"></a>Auswählen von verknüpften Tabellen  
  
> [!NOTE]  
>  Dieser Schritt wird vom Assistenten ausgelassen, falls die Hauptdimensionstabelle keine in der Datenquellensicht definierte Beziehungen zu anderen Dimensionstabellen besitzt.  
  
 Wenn Sie eine Schneeflockendimension erstellen, geben Sie auf der Seite **Verknüpfte Tabellen auswählen** die verknüpften Tabellen an, aus denen zusätzliche Attribute definiert werden. Angenommen, Sie erstellen eine <localizedText>Customer</localizedText>-Dimension, in der Sie eine <localizedText>Customer Geography</localizedText>-Tabelle definieren möchten. In diesem Fall können Sie eine <localizedText>Geography</localizedText>-Tabelle als verknüpfte Tabelle definieren.  
  
## <a name="selecting-dimension-attributes"></a>Auswählen von Dimensionsattributen  
 Nachdem Sie die Dimensionstabellen ausgewählt haben, geben Sie auf der Seite **Dimensionsattribute auswählen** die Attribute an, die Sie in der Dimension aus diesen Tabellen einschließen möchten. Alle zugrunde liegenden Spalten dieser Tabellen sind als potenzielle Dimensionsattribute verfügbar. Das Dimensionsschlüsselattribut muss ausgewählt und zum Durchsuchen aktiviert werden.  
  
 Standardmäßig legt der Assistent den Typ eines Attributs auf `Regular` fest. Unter Umständen empfiehlt es sich jedoch, bestimmte Attribute einem anderen Attributtyp zuzuordnen, der die Daten besser repräsentiert. Die &lt;localizedText&gt;dbo.DimAccount&lt;/localizedText&gt;-Tabelle in der [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW-Beispieldatenbank enthält z. B. eine &lt;localizedText&gt;AccountCodeAlternateKey&lt;/localizedText&gt;-Spalte, die die Kontonummer bereitstellt. Statt den Typ zu `Regular` für dieses Attribut, Sie möchten dieses Attribut zum Zuordnen der `Account Number` Typ.  
  
> [!NOTE]  
>  Wenn der Dimensionstyp und die Standardattributtypen beim Erstellen der Dimension nicht festgelegt sind, können Sie diese Werte mit dem Business Intelligence-Assistenten festlegen, nachdem die Dimension erstellt wurde. Weitere Informationen finden Sie unter [Hinzufügen von Dimensionsintelligenz zu einer Dimension](bi-wizard-add-dimension-intelligence-to-a-dimension.md) oder (bei Dimensionen vom Typ Accounts) [Hinzufügen von Kontointelligenz zu einer Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
 Der Assistent legt den Dimensionstyp automatisch auf Basis der angegebenen Attributtypen fest. In den Assistenten angegebenen Attributtypen die `Type` für die Attribute. Die `Type`-Eigenschafteneinstellungen für die Dimension und ihre Attribute stellen Informationen zum Inhalt einer Dimension für Server- und Clientanwendungen bereit. In einigen Fällen diese `Type` -eigenschafteneinstellungen nur bieten eine Anleitung für Clientanwendungen bereit und sind optional. In anderen Fällen, wie Sie für Konten, Time- oder Currency Dimension, von diese `Type` eigenschafteneinstellungen bestimmen spezifisches Verhalten im Server-basierten und möglicherweise erforderlich, um bestimmte cubeverhalten zu implementieren.  
  
 Weitere Informationen zu Dimensions- und Attributtypen finden Sie unter [Dimensionstypen](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md), [Konfigurieren von Attributtypen](attribute-properties-configure-attribute-types.md).  
  
## <a name="defining-account-intelligence"></a>Definieren der Kontointelligenz  
  
> [!NOTE]  
>  Dieser Schritt wird im Dimensions-Assistenten nur angezeigt, wenn Sie auf der Seite **Dimensionsattribute auswählen** des Assistenten ein **Kontotyp** -Dimensionsattribut definiert haben.  
  
 Zum Erstellen einer Kontotypdimension verwenden Sie die Seite **Kontointelligenz definieren** . Wenn Sie eine Kontotypdimension erstellen, müssen Sie die von [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] unterstützten Standardkontotypen Elementen des Kontotypattributs in der Dimension zuordnen. Diese Zuordnungen werden vom Server verwendet, um separate Aggregationsfunktionen und Aliasnamen für jeden Typ von Kontodaten bereitzustellen.  
  
 Zum Zuordnen dieser Kontotypen stellt der Assistent eine Tabelle mit den folgenden Spalten bereit:  
  
-   In der Spalte **Kontotypen der Quelltabelle** sind die Kontotypen aus der Datenquellentabelle aufgelistet.  
  
-   In der Spalte **Integrierte Kontotypen** sind die vom Server unterstützten Standardkontotypen aufgelistet. Wenn die Quelldaten Standardnamen verwenden, ordnet der Assistent automatisch den Quelltyp dem Servertyp zu und füllt die Spalte **Integrierte Kontotypen** mit diesen Informationen auf. Wenn der Server die Kontotypen nicht zuordnet oder Sie die Zuordnung ändern möchten, wählen Sie einen anderen Typ in der Liste in der Spalte **Integrierte Kontotypen** aus.  
  
> [!NOTE]  
>  Wenn die Kontotypen beim Erstellen einer <localizedText>Accounts</localizedText>-Dimension durch den Assistenten nicht zugeordnet sind, können Sie diese Zuordnungen mit dem Business Intelligence-Assistenten konfigurieren, nachdem die Dimension erstellt wurde. Weitere Informationen finden Sie unter [Hinzufügen von Kontointelligenz zu einer Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).  
  
## <a name="completing-the-wizard"></a>Abschließen des Assistenten  
 Der Assistent durchsucht Dimensionstabellen nach Beziehungen. In Schneeflockendimensionen erstellt der Assistent automatisch Attributbeziehungen zwischen Schlüsselattributen.  
  
 Außerdem erkennt der Assistent automatisch, wenn eine Über-/Unterordnungsbeziehung in der Dimension vorhanden ist. Es ist eine Über-/Unterordnungsbeziehung vorhanden, wenn ein übergeordnetes Attribut auf Elemente des Schlüsselattributs der Dimension verweist. Diese Beziehung definiert hierarchische Beziehungen und Aggregationspfade zwischen den Blattelementen der Dimension. Weitere Informationen zu Über-/Unterordnungshierarchien finden Sie unter [Attribute in über- und untergeordneten Hierarchien](parent-child-dimension-attributes.md).  
  
 Zum Abschließen des Assistenten geben Sie auf der Seite **Assistenten abschließen** einen Namen für die neue Dimension ein und überprüfen die Dimensionsstruktur.  
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen einer Dimension durch Generieren einer Nichtzeittabelle in der Datenquelle](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)   
 [Erstellen einer Zeitdimension durch Generieren einer Zeittabelle](create-a-time-dimension-by-generating-a-time-table.md)   
 [Dimensionsattributeigenschaftenverweis](dimension-attribute-properties-reference.md)   
 [Erstellen einer Zeitdimension durch Generieren einer Zeittabelle](create-a-time-dimension-by-generating-a-time-table.md)   
 [Erstellen einer Dimension durch Generieren einer Nichtzeittabelle in der Datenquelle](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  
