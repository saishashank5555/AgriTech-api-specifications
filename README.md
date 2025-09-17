# AgriTech-api-specifications

openapi: 3.0.0
info:
  title: AgriTech Project
  description: This is AgriTech API documentation.
  version: 1.0.0
  contact:
    name: Sai Shashank
    email: shashank.lingabathini@gmail.com

servers:
  - url: http://localhost:8080
    description: Local Development Server

paths:
  /api/admins/register:
     post:
      summary: Register a new admin
      tags: [Admins]
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/AdminRegisterRequest'
      responses:
        '201':
          description: Admin registered successfully
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Admin registered successfully"
                  adminId:
                   type: integer
                   example: 01
                    
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Admin registration failed"
                  status:
                   type: integer
                   example: 400

        '409':
          description: Conflict - Admin already exists
          content:
            application/json:
              schema:
                type: object
                properties:
                   message:
                    type: string
                    example: "Admin registration failed, Admin already exists"
                   status:
                    type: integer
                    example: 409
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500
                  


  /api/vendors/register:
    post:
      summary: Register a new vendor
      tags: [Vendors]
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/VendorRegisterRequest'
      responses:
        '201':
          description: Vendor registered successfully
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Vendor registered successfully"
                  vendorId:
                   type: integer
                   example: 01
                    
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Vendor registration failed"
                  status:
                   type: integer
                   example: 400

        '409':
          description: Conflict - Vendor already exists
          content:
            application/json:
              schema:
                type: object
                properties:
                   message:
                    type: string
                    example: "Vendor registration failed, Vendor already exists"
                   status:
                    type: integer
                    example: 409
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500

  /api/vendors/getAllproducts/{vendorId}:
    get:
      summary: Get all products by vendor ID
      tags: [Products]
      parameters:
        - in: path
          name: vendorId
          required: true
          schema:
            type: integer
      responses:
        '200':
          description: List of products by vendor
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Product'
                  
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "invalid input"
                  status:
                   type: integer
                   example: 400 
                   
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500         
   
   
  /api/vendors/products/addProduct:                
    post:
      summary: add a new Product
      tags: [Vendors]
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/ProductRegisterRequest'
      responses:
        '201':
          description: Product created successfully
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Product'
          
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Product not added"
                  status:
                   type: integer
                   example: 400 
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500           

   
  /api/getSingleProduct/{productId}:
    get:
      summary: Get product by ID
      tags: [Products]
      parameters:
        - in: path
          name: productId
          required: true
          schema:
            type: integer
      responses:
        '200':
          description: Product details
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/Product'
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "invalid input"
                  status:
                   type: integer
                   example: 400 
        '404':
          description: Product Not Found
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Product Not Found"
                  status:
                   type: integer
                   example: 404
                   
        '500':
         description: Internal Server Error
         content:
          application/json:
            schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500 
                  
  /api/Product/update:              
    put:
      summary: Update product by ID
      tags: [Products]
      requestBody:
        required: true
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/Product'
      responses:
        '200':
          description: Updated product Details
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Product'
                  
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "invalid input"
                  status:
                   type: integer
                   example: 400 
                   
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500 
          
          
  /api/Product/{deleteProductId}:      
    delete:
      summary: Delete product by ID
      tags: [Products]
      parameters:
        - in: path
          name: deleteProductId
          required: true
          schema:
            type: integer
      responses:
        '204':
          description: Product deleted successfully
          
        '400':
          description: Bad Request - Invalid input
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "invalid input"
                  status:
                   type: integer
                   example: 400
        '500':
          description: Internal Server Error
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Internal Server Error"
                  status:
                   type: integer
                   example: 500
        '404':
          description: Product Not Found
          content:
            application/json:
              schema:
                type: object
                properties:
                  message:
                    type: string
                    example: "Product Not Found"
                  status:
                   type: integer
                   example: 404
components:
  schemas:

    AdminRegisterRequest:
      type: object
      properties:
        # CommonDetails fields
        firstName:
          type: string
        lastName:
          type: string
        email:
          type: string
        mobile:
          type: string
        password:
          type: string
          format: password
        preferredLanguage:
          type: string
        role:
          type: string
          enum: [ROLE_ADMIN, ROLE_USER]

        # Address fields
        line1:
          type: string
        village:
          type: string
        district:
          type: string
        state:
          type: string
        pincode:
          type: string
        isPrimary:
          type: boolean
        addressType:
          type: string
        landmark:
          type: string

        # Admin-specific fields
        assignedRegion:
          type: string
        accessLevel:
          type: string
        permissions:
          type: string
        department:
          type: string
        region:
          type: string

    CommonDetails:
      type: object
      properties:
        commonId:
          type: integer
          format: int64
        firstName:
          type: string
        lastName:
          type: string
        email:
          type: string
        mobile:
          type: string
        password:
          type: string
        status:
          type: string
        preferredLanguage:
          type: string
        createdAt:
          type: string
          format: date-time
        updatedAt:
          type: string
          format: date-time
        lastLogin:
          type: string
          format: date-time
        isActive:
          type: boolean
        isDeleted:
          type: boolean

    Admin:
      type: object
      properties:
        adminId:
          type: integer
          format: int64
        firstName:
          type: string
        lastName:
          type: string
        email:
          type: string
        mobile:
          type: string
        password:
          type: string
        role:
          type: string
          enum: [ROLE_ADMIN, ROLE_USER]
        status:
          type: string
        createdAt:
          type: string
          format: date-time
        updatedAt:
          type: string
          format: date-time
        lastLogin:
          type: string
          format: date-time
        isActive:
          type: boolean
        isDeleted:
          type: boolean
        preferredLanguage:
          type: string
        commonDetails:
          $ref: '#/components/schemas/CommonDetails'
        address:
          $ref: '#/components/schemas/Address'

    Vendor:
      type: object
      properties:
        vendorId:
          type: integer
          format: int64
        businessName:
          type: string
        businessType:
          type: string
        registrationNumber:
          type: string
        certifications:
          type: string
        gstNumber:
          type: string
        bankDetails:
          type: string
        warehouseFacilities:
          type: string
        deliveryTieUps:
          type: string
        createdAt:
          type: string
          format: date-time
        updatedAt:
          type: string
          format: date-time
        isActive:
          type: boolean
        commonDetails:
          $ref: '#/components/schemas/CommonDetails'
        address:
          $ref: '#/components/schemas/Address'
        # products:
        #   type: array
        #   items:
        #     $ref: '#/components/schemas/Product'

    Product:
      type: object
      properties:
        productId:
          type: integer
          format: int64
        productName:
          type: string
        description:
          type: string
        category:
          type: string
        price:
          type: number
          format: double
        stock:
          type: integer
        unit:
          type: string
          description: "kg, litre, packet, etc."
        discount:
          type: number
          format: double
        skuCode:
          type: string
        isOrganic:
          type: boolean
        imageUrl1:
          type: string
        imageUrl2:
          type: string
        imageUrl3:
          type: string
        status:
          type: string
          description: "ACTIVE or INACTIVE"
        createdAt:
          type: string
          format: date-time
        updatedAt:
          type: string
          format: date-time
        updatedById:
          type: integer
          format: int64
          description: "Vendor or Admin ID who last updated the product"
        vendor:
          $ref: '#/components/schemas/Vendor'

    Address:
      type: object
      properties:
        addressId:
          type: integer
          format: int64
        street:
          type: string
        city:
          type: string
        state:
          type: string
        postalCode:
          type: string
        country:
          type: string
          
    VendorRegisterRequest:
      type: object
      properties:

        # CommonDetails
        firstName:
          type: string
        lastName:
          type: string
        email:
          type: string
          format: email
        mobile:
          type: string
        password:
          type: string
          format: password
        preferredLanguage:
          type: string
        role:
          type: string
          example: ROLE_VENDOR

        # Address details
        line1:
          type: string
        village:
          type: string
        district:
          type: string
        state:
          type: string
        pincode:
          type: string
        isPrimary:
          type: boolean
        addressType:
          type: string
        landmark:
          type: string

        # Vendor details
        businessName:
          type: string
        businessType:
          type: string
          example: dealer
        registrationNumber:
          type: string
        certifications:
          type: string
        gstNumber:
          type: string
        bankDetails:
          type: string
        warehouseFacilities:
          type: string
          nullable: true
        deliveryTieUps:
          type: string
          nullable: true
        isActive:
          type: boolean
 
          
          
    ProductRegisterRequest:
      type: object
      properties:
        vendorId:
          type: integer
          format: int64
          description: ID of the vendor to link this product with

        productName:
          type: string
        description:
          type: string
        category:
          type: string
        price:
          type: number
          format: double
        stock:
          type: integer
        unit:
          type: string
          description: Unit of measurement (kg, litre, packet, etc.)
        discount:
          type: number
          format: double
          nullable: true
        skuCode:
          type: string
          nullable: true
        isOrganic:
          type: boolean
        imageUrl1:
          type: string
          format: uri
          nullable: true
        imageUrl2:
          type: string
          format: uri
          nullable: true
        imageUrl3:
          type: string
          format: uri
          nullable: true
        status:
          type: string
          enum: [ACTIVE, INACTIVE]      
          
          
          
          
          
          
          
                    
