# Uno a uno

## Uno a uno NO IDENTIFICABLE

![](../../../.gitbook/assets/image%20%2821%29.png)

```sql
CREATE TABLE ejemplo04.pedido (
  numero_pedido SERIAL NOT NULL, 
  fecha_pedido  date NOT NULL, 
  estado        varchar(40) NOT NULL, 
  PRIMARY KEY (numero_pedido));
  
  
CREATE TABLE ejemplo04.factura (
  numero_factura int4 NOT NULL, 
  anio           int4 NOT NULL, 
  fecha_factura  date NOT NULL, 
  forma_pago     varchar(40) NOT NULL, 
  numero_pedido  int4 NOT NULL unique, 
  PRIMARY KEY (numero_factura, 
  anio));
ALTER TABLE ejemplo04.factura ADD CONSTRAINT fk_pedido FOREIGN KEY (numero_pedido) REFERENCES ejemplo04.pedido (numero_pedido);
```

## Uno a uno IDENTIFICABLE

![](../../../.gitbook/assets/image%20%2818%29.png)

```sql
CREATE TABLE cliente
(
    tipo_documento   varchar(20)  NOT NULL,
    numero_documento varchar(50) NOT NULL,
    nombres          varchar(100) NOT NULL,
    apellidos        varchar(100) NOT NULL,
    estado           varchar(20) NOT NULL,
    CONSTRAINT pk_cliente
        PRIMARY KEY (tipo_documento,
                     numero_documento)
);

create table instructor
(
    tipo_documento    varchar(20)  NOT NULL,
    numero_documento  varchar(100) NOT NULL,
    estado_instructor varchar(10)  not null,
    constraint pk_instructor primary key (tipo_documento, numero_documento),
    constraint fk_cliente FOREIGN KEY (tipo_documento, numero_documento) REFERENCES ejemplo04.cliente (tipo_documento, numero_documento)
);
```

## Uno a Uno recursiva

![](../../../.gitbook/assets/image%20%2820%29.png)

```sql
CREATE TABLE categoria (
  numero_categoria SERIAL NOT NULL, 
  categoria_padre  int4 NOT NULL, 
  nombre_categoria varchar(100) NOT NULL, 
  PRIMARY KEY (numero_categoria));
ALTER TABLE categoria ADD CONSTRAINT fk_categoria FOREIGN KEY (categoria_padre) REFERENCES categoria (numero_categoria);
```

Nota: el código de este diseño es equivalente al siguiente, por tal motivo es mejor usar el siguiente ya que el diseño no tendría lógica.

![](../../../.gitbook/assets/image%20%2822%29.png)

```sql
CREATE TABLE categoria (
  numero_categoria SERIAL NOT NULL, 
  categoria_padre  int4 NOT NULL, 
  nombre_categoria varchar(100) NOT NULL, 
  PRIMARY KEY (numero_categoria));
ALTER TABLE categoria ADD CONSTRAINT fk_categoria FOREIGN KEY (categoria_padre) REFERENCES categoria (numero_categoria):

```

