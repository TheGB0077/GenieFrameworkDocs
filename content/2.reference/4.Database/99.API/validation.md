


::alert{type="info"}



::alert{type="info"}



::alert{type="info"}


::ApiCard{object="SearchLight.Validation.ValidationRule" category="Type"}
#docstring


Creates Validation rule for a Model's field

**Examples**

```julia
julia> function not_empty(field::Symbol, m::T)::ValidationResult where {T<:AbstractModel}
         isempty(getfield(m, field)) && return ValidationResult(invalid, :not_empty, "should not be empty")

         ValidationResult(valid)
       end

julia> function is_int(field::Symbol, m::T)::ValidationResult where {T<:AbstractModel}
         isa(getfield(m, field), Int) || return ValidationResult(invalid, :is_int, "should be an int")

         ValidationResult(valid)
       end

julia> function is_unique(field::Symbol, m::T)::ValidationResult where {T<:AbstractModel}
         obj = findone(typeof(m); NamedTuple(field => getfield(m, field))... )
         if ( obj !== nothing && ! ispersisted(m) )
           return ValidationResult(invalid, :is_unique, "already exists")
         end

         ValidationResult(valid)
       end

julia> ValidationRule(:username, not_empty)
julia> ValidationRule(:username, is_unique)
julia> ValidationRule(:age, is_int)
julia> ValidationRule(:email, not_empty)
```


<a target='_blank' href='https://github.com/GenieFramework/SearchLight.jl/blob/253c0708b400b53469e33ac984a0b386afe486e0/src/Validation.jl#L32-L63' class='documenter-source'>source</a><br>

::
::ApiCard{object="SearchLight.Validation.ModelValidator" category="Type"}
#docstring


The object that defines the rules and stores the validation errors associated with the fields of a `model`.


<a target='_blank' href='https://github.com/GenieFramework/SearchLight.jl/blob/253c0708b400b53469e33ac984a0b386afe486e0/src/Validation.jl#L74-L76' class='documenter-source'>source</a><br>

::

::alert{type="info"}


::ApiCard{object="SearchLight.Validation.validate" category="Function"}
#docstring


```julia
validate(m::T)::Bool where {T<:AbstractModel}
```

Validates `m`'s data. A `bool` is return and existing errors are pushed to the validator's error stack.


<a target='_blank' href='https://github.com/GenieFramework/SearchLight.jl/blob/253c0708b400b53469e33ac984a0b386afe486e0/src/Validation.jl#L96-L100' class='documenter-source'>source</a><br>

::

::alert{type="info"}



::alert{type="info"}



::alert{type="info"}



::alert{type="info"}



::alert{type="info"}

